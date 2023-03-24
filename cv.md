# Иван Бережной
***


## Контакты

* Telegram: @john_ber
* Email: johnber1152@gmail.com


## Обо мне
Проходил курсы по на Udemy (фронтенд, фигма). Самостоятельно изучал php.

Работаю на фрилансе чуть более года. В основном занимаюсь проектами по дополнениям / исправлениям на уже готовых сайтах. 
Несколько раз занимался разработкой сайтов с нуля (фронт + бэк). 
В портфолио есть проект по аренде атвомобилей с обширным функционалом и панелью администратора.

Помимо курсов, изучал алгоритмы и структуры данных на питоне по публичным записям лекций МФТИ.

После прохождения этого курса надеюсь устроиться на постоянную должность, из-за проблем со стабильностью на фрилансе.


## Мои навыки:

* HTML 
* JS 
    + JQuery
* CSS 
    + SASS / LESS
    + Bootstrap
    + БЭМ методология
* PHP
* Python 
    + BS4
    + Selenium

## Пример кода
Это решение задачи, где на вход даются данные о блюдах и ингредиянтах для их изготовления, вида:
```
dishes = [["Salad", "Tomato", "Cucumber", "Salad", "Sauce"],
            ["Pizza", "Tomato", "Sausage", "Sauce", "Dough"],
            ["Quesadilla", "Chicken", "Cheese", "Sauce"],
            ["Sandwich", "Salad", "Bread", "Tomato", "Cheese"]]
```


Функция должна вернуть массив, где каждый элемент начинается с ингредиента, а за ним следуют все блюда, которые из него готовятся (в алфавитном порядке).

Вывод для должен быть:
```
solution(dishes) = [["Cheese", "Quesadilla", "Sandwich"],
                      ["Salad", "Salad", "Sandwich"],
                      ["Sauce", "Pizza", "Quesadilla", "Salad"],
                      ["Tomato", "Pizza", "Salad", "Sandwich"]]
```


При условии, что:
1 ≤ dishes.length ≤ 500,
2 ≤ dishes[i].length ≤ 10,
1 ≤ dishes[i][j].length ≤ 50

Вот пример моего решения:
```
function solution(dishes) {
    let ingredients = new Set();
    let unique = new Set();
    for(let d = 0; d < dishes.length; d++){
        for(let i = 1; i < dishes[d].length; i++){
            if(!ingredients.has(dishes[d][i])){
                ingredients.add(dishes[d][i]);   
            }else{
                unique.add(dishes[d][i]);
            }
        }
    }
    unique = Array.from(unique).sort();
    for(let u = 0; u < unique.length; u++){
        let iList = new Set();
        for(let d = 0; d < dishes.length; d++){
            for(let i = 1; i < dishes[d].length; i++){
                if(dishes[d][i] == unique[u]){
                    iList.add(dishes[d][0]);
                    break;
                }
            }
        }
        unique[u] = [unique[u]].concat(Array.from(iList).sort());
    }
    return unique;
}
```

