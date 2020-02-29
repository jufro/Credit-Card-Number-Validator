﻿# Отчёт о тестировании Credit Card Number Validator
### Краткое описание
29.02.2020 было проведено функциональное тестирование приложения Credit Card Number Validator.

На тестирование затрачено: 1 час

В результате тестирования дефекты не выявлены.

### Описание процесса тестирования

В процессе тестирования использовались следующие артефакты:

* тест-кейсы: https://docs.google.com/spreadsheets/d/1qQ8cYYtzq9dROnGkt6wNoHIsqSonxbytO9BSth8cV2A/edit?usp=sharing
* отчёт о тестировании

В качестве тестовых данных использовались данные https://github.com/netology-code/javaqa-homeworks/blob/master/intro/idea.md

код программы:

```java
public class Main {
  public static void main(String[] args) {
    
    String number = "5351719427810741";
    System.out.println(String.format("Result is %s", isValidCardNumber(number) ? "OK" : "FAIL"));
  }

  public static boolean isValidCardNumber(String number) {
    if (number == null) {
      return false;
    }

  public static boolean isValidCardNumber(String number) {
    if (number == null) {
      return false;
    }

    if (number.length() != 16) {
      return false;
    }

    long result = 0;
    for (int i = 0; i < number.length(); i++) {
      int digit;
      try {
        digit = Integer.parseInt(number.charAt(i) + "");
      } catch (NumberFormatException e) {
        return false;
      }

      if (i % 2 == 0) {
        digit *= 2;
        if (digit > 9) {
          digit -= 9;
        }
      }
      result += digit;
    }

    return (result != 0) && (result % 10 == 0);
  }
}
```

Тестирование производилось в следующем окружении:

* ОС Windows 10 x64
* Java 11.0.6
* IntelliJ IDEA 2019.3.3
* git version 2.25.0.