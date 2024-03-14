<div align='center'>
   <img src="https://media.giphy.com/media/hvRJCLFzcasrR4ia7z/giphy.gif" width="30px"/>
</div>

### В ходе проекта проведём:

*   А/B тестирование

  Новая механика оплаты VS базовая механика оплаты на сайте.
  
*  На основе тестирования сделаем выводы, стоит ли запускать новую механику оплаты на всех пользователей.

---

<details>
  <summary><b> 🛠 &nbsp;&nbsp;Используемые данные:&nbsp;</b></summary>
  <br/> 
<div>
<details>
  <summary><b>&nbsp;&nbsp;olist_customers_datase.csv — таблица с уникальными идентификаторами пользователей&nbsp;</b></summary>
  
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

