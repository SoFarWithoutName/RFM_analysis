<div align='center'>
<h1>
  Когортный и RFM анализы!
  <img src="https://media.giphy.com/media/hvRJCLFzcasrR4ia7z/giphy.gif" width="30px"/>
</h1>
</div>
<div align='center'>
   <img src="https://img.shields.io/badge/Python-%23AFEEEE?style=for-the-badge&logo=Python&logoColor=yellow"/>
   <img src="https://img.shields.io/badge/pandas-%23AFEEEE?style=for-the-badge&logo=pandas&logoColor=white"/>
   <img src="https://img.shields.io/badge/Seaborn-%23AFEEEE?style=for-the-badge&logo=Seaborn"/>
   <img src="https://img.shields.io/badge/matplotlib-%23AFEEEE?style=for-the-badge&logo=matplotlib&logoColor=white"/>
   <img src="https://img.shields.io/badge/numpy%20-%23AFEEEE?style=for-the-badge&logo=numpy%20&logoColor=white"/>
</div>

## В ходе проекта проведём анализ совершенных покупок и ответим на следующие вопросы:

### Сколько пользователей совершили покупку только один раз?

Пользователи совершившие покупку только один раз - будут те пользователи, у которых есть данные о "подтверждении оплаты заказа", т.е. которые хоть раз оплачивали товар. Покупкой является оплата товара - дальнейшая судьба этого заказа (Возврат, недоступен и т.д.) "это уже совсем другая история"

  ![image](https://github.com/KinderDs/Example/assets/163444205/86e669b7-3378-4f7b-906f-8478cc6409f9)

### Сколько заказов в месяц в среднем не доставляется по разным причинам?
  
Доставленными заказами будут являться только те заказы, статус которых "delivered" и в столбце "время доставки заказа" стоит дата. По остальным же рассмотрим детализацию.

![image](https://github.com/KinderDs/Example/assets/163444205/7637da47-8f24-4748-abb3-78c150f6eb8b)
  
### В какой день недели каждый товар чаще всего покупается?

Частота покупки товара по дню недели записаны в third_zd_3 (если нас интересуют дубликаты по товарам, например присутствует товар у которого частота одинакова в 6 разных днях неделях) и third_zd_33 (без дубликатов, только максимальные числа).

*  third_zd_3
  
  ![image](https://github.com/KinderDs/Example/assets/163444205/de6cd185-c2a9-4c79-83c0-1f1d5acc51a0)

*  third_zd_33

![image](https://github.com/KinderDs/Example/assets/163444205/fe3e8dcd-6716-4633-93d7-e106a59e3435)


### Сколько у каждого из пользователей в среднем покупок в неделю (по месяцам)?

![image](https://github.com/KinderDs/Example/assets/163444205/6e466b66-97bb-4dd9-89c6-4be40d13ef98)


### Проведём когортный анализ пользователей и определим когорту с самым высоким retention на 3й месяц в период с января по декабрь.

В период с января по декабрь когорта с самым высоким retention на 3й месяц является июнь (2017-06-01) со значением равным 0.004141

![image](https://github.com/KinderDs/Example/assets/163444205/468f8156-5325-48df-8a58-4a7b44195791)



### Построим RFM-сегментацию пользователей.

![image](https://github.com/KinderDs/Example/assets/163444205/705c9e51-5657-42b4-9582-2a07be837a0f)

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
