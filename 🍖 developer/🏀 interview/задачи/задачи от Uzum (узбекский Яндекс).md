// Микросервис чеков высоконагруженного маркетплейса, десятки тысяч заказов в сутки.
// Основная функция микросервиса - отправка чеков в налоговую (во внешний независимый сервис)
// Инфраструктура - Kubernetes 8 подов (реплик), высоконагруженный.
// TaxClient - клиент налоговой (feign) - timeout = 60 секунд (не наш, не можем повлиять)
@Slf4j
@Service
@RequiredArgsConstructor
public class SomeServiceImpl implements SomeService {
    private final TaxClient taxClient;
    private final ReceiptDao receiptDao;
    private final ReceiptSourceDao receiptSourceDao;
    
    @Setter
    private SomeService self;
     
    @Override
    @Transactional
    @Scheduled(cron = "${cron.expression}")  // "30 30 * * *"
    public void processJobRunning() {
        Page  page = new Page(0,100);
        List<Receipt> receipts = self.getRefundReceipts(page);
         
        for (Receipt receipt : receipts){
            receipt.setProcessed(true);
            receiptDao.save(receipt);
            try {
                var receiptDto = new ReceiptDto(receipt.getId(), receipt.getSum());
                taxClient.idempotentSendReceipt(receiptDto, getReceiptSource(receipt));
            } catch(Exception e) {
                log.error("Error occured while sending receipt to tax client ", e);
            }
        }
    }
     
    @Transactional(readOnly = true)
    public List<Receipt> getRefundReceipts(Page page) {
        return receiptDao.findAllBySourceAndProcessedFalse(ReceiptSource.REFUND, page); // select * from receipt where source = 'REFUND' and processed = false;
    }
     
    @Cacheable(value = "receipt_type", cacheManager = "redisCacheManager") // по сути работает как hashMap
    @Transactional(readOnly = true)
    public ReceiptSource getReceiptSource(Receipt receipt) {
        return receiptSourceDao.findSourceByReceiptId(receipt.getId()); // select source from receipt_source where receipt_id = id;
    }
}
 
public interface ReceiptDao extends JpaRepository<Receipt, Long> {
    List<Receipt> findAllBySourceAndProcessedFalse(ReceiptSource source, page);
}
 
public interface ReceiptSourceDao extends JpaRepository<ReceiptSource, Long> {
    ReceiptSource findSourceByReceiptId(Long receiptId);
}
 
//ниже этой строки - все корректно - enum, dto, entity - только для наглядности
@Entity
@AllArgsConstructor
@NoArgsConstructor
@Data
public class Receipt {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private boolean processed;
    private String sum;
    private ReceiptSource source;
}
 
@AllArgsConstructor
@NoArgsConstructor
@Data
@Entity
public enum ReceiptSource {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private Long receiptId; //id from receipt
    private ReceiptSourceType source;
}
 
public enum ReceiptSourceType {
    DISCOUNT,
    SELL,
    REFUND
} 
 
@Data
@NoArgsConstructor
public class ReceiptDto {
    private Long id;
    private String sum;
    private ReceiptSource source;
}










create table department
(
  id  bigserial
    primary key,
  name varchar(255) not null
);

create table employee
(
  id            bigserial,
  name          varchar(255) not null,
  salary        bigint    not null,
  department_id bigint    not null constraint fkagvsnbka5p21h7ejh8ox606hv
      references department
);


select dep.name, employee.salary, count(employee.id) from employee
inner join department dep on employee.department_id = department.id
group by dep.name, employee.salary
having count(employee.id) >3

Результат:
Dep1  1000 - 3 сотрудника
Dep1  2000 - 4 сотрудника
Dep12 2000 - 3 сотрудника




id = 1, price = 1000
@Transactional(isolation = Isolation.REPEATABLE_READ)
{
    var product = productDao.findById(id);
    var newPrice =  product.getPrice - 100; //вычисляется очень долго (сложная логика)
    product.setPrice(newPrice);
    productDao.save(product);
}







