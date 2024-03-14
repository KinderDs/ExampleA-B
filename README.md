<div align='center'>
   <img src="https://media.giphy.com/media/hvRJCLFzcasrR4ia7z/giphy.gif" width="30px"/>
</div>

### В ходе проекта проведём А/В тестирование новой механики оплаты VS базовая механика оплаты на сайте. 
### А так же ответим на следующие вопросы:

*   Имеются ли различия в показателях и с чем они могут быть связаны?

*   Являются ли эти различия статистически значимыми?
  
*  Стоит ли запускать новую механику на всех пользователей?

### P.S. Реализуем функцию, которая:

*   Автоматически подгружает информацию из дополнительного файла;
*   Пересчитывает метрики;
*   Строит графики по получаемым метрикам.

---

<details>
  <summary><b> 🛠 &nbsp;&nbsp;Используемые данные:&nbsp;</b></summary>
  <br/> 
<div>
<details>
  <summary><b>&nbsp;&nbsp;groups.csv - файл с информацией о принадлежности пользователя к контрольной или экспериментальной группе (А – контроль, B – целевая группа)&nbsp;</b></summary>
groups.csv - файл с информацией о принадлежности пользователя к контрольной или экспериментальной группе (А – контроль, B – целевая группа) 
groups_add.csv - дополнительный файл с пользователями, который вам прислали спустя 2 дня после передачи данных
active_studs.csv - файл с информацией о пользователях, которые зашли на платформу в дни проведения эксперимента. 
checks.csv - файл с информацией об оплатах пользователей в дни проведения эксперимента. 
  
* customer_id — позаказный идентификатор пользователя

* customer_unique_id —  уникальный идентификатор пользователя  (аналог номера паспорта)

*  customer_zip_code_prefix —  почтовый индекс пользователя

*  customer_city —  город доставки пользователя

*  customer_state —  штат доставки пользователя


</details>


<details>
  <summary><b>&nbsp;&nbsp;olist_orders_dataset.csv —  таблица заказов&nbsp;</b></summary>
  
*  order_id —  уникальный идентификатор заказа (номер чека)

*  customer_id —  позаказный идентификатор пользователя
  
*  order_status —  статус заказа
  
*  order_purchase_timestamp —  время создания заказа
  
*  order_approved_at —  время подтверждения оплаты заказа
  
*  order_delivered_carrier_date —  время передачи заказа в логистическую службу
  
*  order_delivered_customer_date —  время доставки заказа
  
*  order_estimated_delivery_date —  обещанная дата доставки

</details>

<details>
  <summary><b>&nbsp;&nbsp;olist_order_items_dataset.csv —  товарные позиции, входящие в заказы&nbsp;</b></summary>
  
*  order_id —  уникальный идентификатор заказа (номер чека)
  
*  order_item_id —  идентификатор товара внутри одного заказа
   
*  product_id —  ид товара (аналог штрихкода)
   
*  seller_id — ид производителя товара
   
*  shipping_limit_date —  максимальная дата доставки продавцом для передачи заказа партнеру по логистике
   
*  price —  цена за единицу товара
  
*  freight_value —  вес товара
</details>
</div>
</details>

---
### Стек:
![Python](https://img.shields.io/badge/Python-%23AFEEEE?style=for-the-badge&logo=Python&logoColor=yellow)
![Pandas](https://img.shields.io/badge/pandas-%23AFEEEE?style=for-the-badge&logo=pandas&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-%23AFEEEE?style=for-the-badge&logo=Seaborn)
![matplotlib](https://img.shields.io/badge/matplotlib-%23AFEEEE?style=for-the-badge&logo=matplotlib&logoColor=white)
![numpy](https://img.shields.io/badge/numpy%20-%23AFEEEE?style=for-the-badge&logo=numpy%20&logoColor=white)

