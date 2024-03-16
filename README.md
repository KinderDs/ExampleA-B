<div align='center'>
   <img src="https://media.giphy.com/media/hvRJCLFzcasrR4ia7z/giphy.gif" width="30px"/>
</div>
Решили протестировать как и на что повлияет новая механика оплаты на сайте. 

### В ходе проекта проведём А/В тестирование новой механики оплаты VS базовая механика оплаты на сайте. 

## Проведём разведочный анализ данных EDA.
В ходе анализа данных обнаружил, что в нашем общем датасете есть пользователи, которых система регистрирует как незаходящих на платформу (149 пользователей), НО! при этом фиксируется факт оплаты.
### Вывод:
Проанализоровав данные этих пользователей, выявил, что эти пользователи распределены не равномерно между группами, большинство (120) пользователей принадлежит целевой группе, а 29 пользователей контрольной. Так же суммы оплаты имеют разные значения - 13 уникальных значений.

   *   Система дала сбой и не зафиксировала факт посещения платформы.

   *   Транзакция была зафиксирована уже после введения новой фичи.

   *   Оплата с других ресурсов, либо автоматическое списание.

Не владеем полным спеком данных и возможности обговорить с заказчиком, считаю, что раз уж количество пользователей имеет большой перевес в сторону целевой группы - то это может повлиять на данные. Далее будем игнорировать эти данные.
### Пропущенные значения:
При проверки на пропущенные значения полного датасета, обнаружил пропуски (это связано с тем, что мы добавили доход с каждого пользователя, но многие не платили).
Заменим значения Nan в rev на нули и создадим булевую колонку (1 - была покупка, 0 - нет) для удобства расчётов.

## Далее ответим на следующие вопросы:

### На какие метрики обращать внимание?

В первую очередь в данном эксперименте нужно обратить внимание на Conversion Rate, так как она показывает сколько пользователей совершили конверсионное действие: тестируем новую механику оплаты - следовательно это факт оплаты.
Дополнительной метрикой буду рассматривать Average Order Value - средний чек.

### Имеются ли различия в показателях и с чем они могут быть связаны?
Конверсия в покупку между группами имеет небольшую разность.


<div align='centre'>
   <img src="https://github.com/KinderDs/ExampleA-B/assets/163444205/8bd1c433-4d25-4d3f-9842-e8b23230026d" width ="500" height="350">
</div>

<div align='centre'>
   <img src="https://github.com/KinderDs/ExampleA-B/assets/163444205/4c03153b-80b5-43fc-a993-94fcfa780764" width ="500" height="350">
</div>


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
   
*   groups.csv - файл с информацией о принадлежности пользователя к контрольной или экспериментальной группе (А – контроль, B – целевая группа)
   
*   groups_add.csv - дополнительный файл с пользователями, который прислали спустя 2 дня после передачи данных
  
*   active_studs.csv - файл с информацией о пользователях, которые зашли на платформу в дни проведения эксперимента.
  
*   checks.csv - файл с информацией об оплатах пользователей в дни проведения эксперимента.
  
</details>

---

### Стек:
![Python](https://img.shields.io/badge/Python-%23AFEEEE?style=for-the-badge&logo=Python&logoColor=yellow)
![Pandas](https://img.shields.io/badge/pandas-%23AFEEEE?style=for-the-badge&logo=pandas&logoColor=white)
![scipy](https://img.shields.io/badge/scipy-%23AFEEEE?style=for-the-badge&logo=scipy&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-%23AFEEEE?style=for-the-badge&logo=Seaborn)
![matplotlib](https://img.shields.io/badge/matplotlib-%23AFEEEE?style=for-the-badge&logo=matplotlib&logoColor=white)
![numpy](https://img.shields.io/badge/numpy%20-%23AFEEEE?style=for-the-badge&logo=numpy%20&logoColor=white)
![pingouin](https://img.shields.io/badge/pingouin-%23AFEEEE?style=for-the-badge&logo=pingouin&logoColor=white)

