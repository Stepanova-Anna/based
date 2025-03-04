# Лабораторная работа 2. Схема данных. EER-диаграмма

> Задание 1. Повторите действия, демонстрируемые в ролике и создайте диаграмму (модель), созданную во второй половине ролика. Экспортируйте модель в виде изображения, экспортируйте модель в виде SQL-скрипта. В отчете требуется отобразить:схему в виде изображения;скопированный запрос, соответствующий созданию этой базы данных: вставьте его в какой-либо сервис для хранения фрагментов кода (gist), сгенерируйте публичную ссылку и вставьте её в отчёт; фрагмент запроса, касающийся создания и настройки таблицы invoice.

**Результат:**

![ЛР2.Задание 1](https://github.com/Stepanova-Anna/based/blob/main/LR2/firstModel.png)
[Ссылка на gist](https://gist.github.com/Stepanova-Anna/232b54ce15d586cb75ab67a391848c50)
```
-- -----------------------------------------------------
-- Table `firstModel`.`invoice`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `firstModel`.`invoice` (
  `idinvoice` INT NOT NULL AUTO_INCREMENT,
  `user_id` INT NOT NULL,
  `product_id` INT NOT NULL,
  `cost` DECIMAL(10,2) NOT NULL,
  PRIMARY KEY (`idinvoice`),
  INDEX `user_idx` (`user_id` ASC) VISIBLE,
  INDEX `product_idx` (`product_id` ASC) VISIBLE,
  CONSTRAINT `user`
    FOREIGN KEY (`user_id`)
    REFERENCES `firstModel`.`user` (`id`)
    ON DELETE CASCADE
    ON UPDATE CASCADE,
  CONSTRAINT `product`
    FOREIGN KEY (`product_id`)
    REFERENCES `firstModel`.`product` (`idproduct`)
    ON DELETE CASCADE
    ON UPDATE CASCADE)
ENGINE = InnoDB;
```
---

> Задание 2. Создайте собственную EER-диаграмму и спроектируйте БД с параметрами на основе текста, опубликованного по ссылке: https://habr.com/ru/post/175985/
> Экспортируйте полученную модель в виде изображения, экспортируйте модель в виде SQL-скрипта.
> В отчете требуется отобразить: 
> - схему в виде изображения;
> - скопированный запрос, соответствующий созданию этой базы данных: вставьте его в какой-либо сервис для хранения фрагментов кода (gist), сгенерируйте публичную или секретную ссылку и вставьте её в отчёт;
> - фрагмент запроса, касающийся создания и настройки таблицы Orders.

**Результат:**

[Ссылка на gist](https://gist.github.com/Stepanova-Anna/7e7c92dd019e6de11184895bf85ebc59)

![ЛР2.Задание 2](https://github.com/Stepanova-Anna/based/blob/main/LR2/Connect.png)

```
-- -----------------------------------------------------
-- Table `mydb`.`Orders`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `mydb`.`Orders` (
  `id` INT NOT NULL AUTO_INCREMENT,
  `shop_id` INT NOT NULL,
  `product_id` INT NOT NULL,
  `fio` INT NOT NULL,
  `date` DATE NULL,
  `quantity` TINYINT NULL,
  `tel` VARCHAR(100) NULL,
  `confirm` TINYINT NULL,
  PRIMARY KEY (`id`, `shop_id`, `product_id`, `fio`),
  UNIQUE INDEX `id_UNIQUE` (`id` ASC) VISIBLE,
  INDEX `orders_to_users_idx` (`fio` ASC) VISIBLE,
  INDEX `orders_to_shops_idx` (`shop_id` ASC) VISIBLE,
  INDEX `orders_to_products_idx` (`product_id` ASC) VISIBLE,
  CONSTRAINT `orders_to_users`
    FOREIGN KEY (`fio`)
    REFERENCES `mydb`.`users` (`id`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION,
  CONSTRAINT `orders_to_shops`
    FOREIGN KEY (`shop_id`)
    REFERENCES `mydb`.`Shops` (`id`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION,
  CONSTRAINT `orders_to_products`
    FOREIGN KEY (`product_id`)
    REFERENCES `mydb`.`Products` (`id`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION,
  CONSTRAINT `orders_to_deliveries`
    FOREIGN KEY (`id`)
    REFERENCES `mydb`.`Deliveries` (`order_id`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;
```

---

> Задание 3. Выполните операцию Database - Forward Engineer и создайте базу данных на вашем сервере. Сделайте скриншот с успешным выполнением этого процесса и вставьте его в отчет. 

**Результат:**


![ЛР2.Задание 3](https://github.com/Stepanova-Anna/based/blob/main/LR2/Task_3.png)

---

> Задание 4. Добавьте несколько строк и новых атрибутов в каждую таблицу созданной базы данных. Попробуйте удалить связанные в нескольких таблицах данные, зафиксируйте, что произошло и опишите текстом (и по возможности дополните скриншотами) в отчёте.

**Результат:**

![ЛР2.Задание 4](https://github.com/Stepanova-Anna/based/blob/main/LR2/T4.3.png)
![ЛР2.Задание 4.4](https://github.com/Stepanova-Anna/based/blob/main/LR2/T4.4.png)

