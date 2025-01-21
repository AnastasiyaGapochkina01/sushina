1) Запаковать приложение https://github.com/AnastasiyaGapochkina01/web-go в docker с помощью multistage build и запустить с помощью docker compose
2) Запаковать Java App в docker с помощью multistage build и запустить с помощью docker compose
```
package com.example;

public class App {
    public static void main(String[] args) {
        System.out.println("Hello, Multi-Stage Docker Build!");
    }
}
```
3) Для всех задач из домашки https://github.com/AnastasiyaGapochkina01/sushina/blob/main/home-work-11.md#%D0%B7%D0%B0%D0%B4%D0%B0%D0%BD%D0%B8%D1%8F-docker-compose для всех контейнеров с базами данными добавить healthcheck в docker compose
4) Придумать и реализовать healthcheck для nginx и внедрить его в image nginx
