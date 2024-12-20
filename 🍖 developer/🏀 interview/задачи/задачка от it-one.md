
# задание
/**  
 * Напишите функцию на Java, которая проверяет, являются ли две заданные строки анаграммами (только английский алфавит). * Две строки являются анаграммами, если они содержат одинаковые символы в одинаковом количестве, * игнорируя пробелы и регистр букв. * Требования: * Функция должна принимать две строки в качестве входных параметров. * Функция должна возвращать true, если строки являются анаграммами, и false в противном случае. * Функция должна игнорировать регистр символов и пробелы. * Примеры: * Входные данные: "Listen" и "Silent" * Выход: true (потому что "Listen" и "Silent" содержат одинаковые буквы) * Входные данные: "Hello" и "Olelh" * Выход: true * Входные данные: "Test" и "Taste" * Выход: false * Указания: * Убедитесь, что ваша функция работает за оптимальное время и использует минимальное количество памяти. * Протестируйте вашу функцию на различных строках, включая пустые строки и строки с пробелами. * Опишите, почему ваше решение является оптимальным и какие могут быть потенциальные ограничения. * ----------------------------------------------------------------------------------------------- */


# мое решение 

```java
import java.util.HashMap;  
import java.util.Map;  
  
public class Main {  
  
    public static void main(String arg[]) {  
        System.out.println(isAnagram("Listen", "listen "));  
    }  
    public static boolean isAnagram(String value1, String value2) {  
        if (value1 == null && value2 == null) {  
            return false;  
        } else if ("".equals(value1) && "".equals(value2)) {  
            return true;  
        } else {  
            Map<String, Integer> stract1 = getStract(value1);  
            Map<String, Integer> stract2 = getStract(value2);  
            if (stract1.size() != stract2.size()){  
                return false;  
            }  
            for (Map.Entry<String, Integer> pare : stract1.entrySet()){  
               Integer checkValue = stract2.get(pare.getKey());  
               if(checkValue!=pare.getValue()){  
                   return false;  
               }  
            }  
        }  
        return true;  
    }  
    private static Map<String, Integer> getStract(String value) {  
        Map<String, Integer> stract = new HashMap<>();  
        char[] ar = value.toCharArray();  
        for (int i = 0; i < ar.length; i++) {  
            char v = ar[i];  
            String stringValue = String.valueOf(v).toLowerCase();  
            if(" ".equals(stringValue)){  
                continue;  
            }  
            if (stract.containsKey(stringValue)) {  
                Integer count = stract.get(stringValue);  
                stract.put(stringValue, count + 1);  
            } else {  
                stract.put(stringValue, 1);  
            }  
        }  
        return stract;  
    }  
}
```