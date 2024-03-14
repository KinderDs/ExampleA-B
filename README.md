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
*   groups.csv - файл с информацией о принадлежности пользователя к контрольной или экспериментальной группе (А – контроль, B – целевая группа) 
*   groups_add.csv - дополнительный файл с пользователями, который вам прислали спустя 2 дня после передачи данных
*   active_studs.csv - файл с информацией о пользователях, которые зашли на платформу в дни проведения эксперимента. 
*   checks.csv - файл с информацией об оплатах пользователей в дни проведения эксперимента. 
</details>
---
### Стек:
![Python](https://img.shields.io/badge/Python-%23AFEEEE?style=for-the-badge&logo=Python&logoColor=yellow)
![Pandas](https://img.shields.io/badge/pandas-%23AFEEEE?style=for-the-badge&logo=pandas&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-%23AFEEEE?style=for-the-badge&logo=Seaborn)
![matplotlib](https://img.shields.io/badge/matplotlib-%23AFEEEE?style=for-the-badge&logo=matplotlib&logoColor=white)
![numpy](https://img.shields.io/badge/numpy%20-%23AFEEEE?style=for-the-badge&logo=numpy%20&logoColor=white)

