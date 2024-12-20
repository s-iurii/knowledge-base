вывести в консоль тип машины и количество в типе из данного списка.
```java
public class CarType {
    private String type;

    public CarType(String type) {
        this.type = type;
    }

    public String getType() {
        return type;
    }

    @Override
    public String toString() {
        return type;
    }
}


public class Car {
    private String name;
    private CarType carType;

    public Car(String name, CarType carType) {
        this.name = name;
        this.carType = carType;
    }

    public CarType getCarType() {
        return carType;
    }

    @Override
    public String toString() {
        return name + " (" + carType + ")";
    }
}


CarType sedan = new CarType("Sedan");
        CarType suv = new CarType("SUV");
        CarType truck = new CarType("Truck");

        // Создадим несколько машин
        List<Car> cars = Arrays.asList(
            new Car("Car1", sedan),
            new Car("Car2", suv),
            new Car("Car3", sedan),
            new Car("Car4", truck),
            new Car("Car5", suv),
            new Car("Car6", sedan)
        );

```


# решение

 ```java
 import java.util.*;
import java.util.stream.Collectors;

public class Main {
    public static void main(String[] args) {
        // Создадим несколько типов машин
        CarType sedan = new CarType("Sedan");
        CarType suv = new CarType("SUV");
        CarType truck = new CarType("Truck");

        // Создадим несколько машин
        List<Car> cars = Arrays.asList(
            new Car("Car1", sedan),
            new Car("Car2", suv),
            new Car("Car3", sedan),
            new Car("Car4", truck),
            new Car("Car5", suv),
            new Car("Car6", sedan)
        );

        // Группируем машины по типу и считаем количество каждой группы
        Map<CarType, Long> carCountByType = cars.stream()
            .collect(Collectors.groupingBy(Car::getCarType, Collectors.counting()));

        // Выводим результат
        carCountByType.forEach((carType, count) -> 
            System.out.println(carType.getType() + ": " + count)
        );
    }
}

```