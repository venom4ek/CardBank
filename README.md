# Тестирование программы по проверке банковских карт

> ## **Тест план:**
 >1. произвести установку IntelliJ IDEA по [инструкции](https://github.com/netology-code/javaqa-homeworks/blob/master/intro/idea.md "нажмите для перехода")
 >1. Проверить работу этой программы
>
<details>

```java
public class Main {
  public static void main(String[] args) {
    // TODO: подставлять номер карты нужно сюда между двойными кавычками, без пробелов
    String number = "5351719427810741";
    System.out.println(String.format("Result is %s", isValidCardNumber(number) ? "OK" : "FAIL"));
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

</details>

> 3. отправить отчет/багрепорт о проверке.

***

> ## **Отчет:**
>
> ### установка IntelliJ IDEA. 
>1. В инструкции по установке IDEA, в шаге №19 битая ссылка. создан issue #1
>1. Проверка работы программы: 
>
>- при вводе номера любой карты, после запуска программы получаем Result is FAIL. создан issue #2

***

>#### Время потраченное на тестирование 20 минут, с учетом установки Java SDK.
>
>##### было проведено дымовое тестирование для подтверждения, что программа выполняет свои основные функции. 