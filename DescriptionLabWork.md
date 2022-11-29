# Лабораторная работа №1 по курсу: ***"Машинное обучение для задач информационной безопасности"***.

Лабораторную работу выполнил студент группы 6233 Мелешнко Иван.  

## Задание на лабораторную работу
1. Базовый контест (делают все хоть как-то)
    - Обучить модель без каких-либо дополнительных условий, которая должна наилучшим образом отработать на тестовой выборке преподавателя с точки зрения F-меры
2. Вторичные контесты
    - Максимально логичным образом обучить качественную модель, использующую для работы только 10 признаков из всего исходного множества.
    - Обучить модель, обеспечивающую вероятность пропуска бота на уровне не выше 0.03, и имеющую насколько возможно низкую вероятность ложного обнаружения.
3. Углубленное аналитическое исследование по имеющимся данным
    - Тем или иным способом выполнить сравнительное исследование значимости различных признаков применительно к произвольному фиксированному классификатору.
    - Синтезировать 3 или более собственных признаков на основе имеющихся и показать, что они имеют какие-либо преимущества перед хотя бы какими либо из базовых признаков.
    - Выбрать один базовый тип ML-модели на свой вкус (SVM, дерево решений, случайный лес, градиентный бустинг и пр.) и провести ROC-анализ в зависимости от её гиперпараметров.
    - Провести исследование влияние параметров обучения на недо- и переобученность модели.

# Выполнение пунктов лабораторной работы

1. Базовый контест (делают все хоть как-то)
    - ***Обучить модель без каких-либо дополнительных условий, которая должна наилучшим образом отработать на тестовой выборке преподавателя с точки зрения F-меры***

    * 1. На данном этапе для исследования моделей использовался пул из трех стандартных и самых распространненных классификатора из пакета **sklearn**:
        * ***Метод k-ближайших соседей (K-Nearest Neighbors);***
        * ***Случайный лес (Random Forests);***
        * ***Наивный байесовский метод (Naive Bayes);***
    * 2. Данные были загружены из файлов и разделены в процентном соотношении 40/60, где 40% процентов данных используется для тестовой выборки, а 60% для обучения.
    * 3. После чего, модели были обучены и протестированы, на данных, которые были разделены на предыдущем шаге.
        * Для оценки моделей использовались следующие метрики:
            - Precision,  F1-score, confusion_matrix, а так же метрики из classification_report 
    * 4. При анализе результатов, оказалось, что только RandomForestClassifier удовлетворяет заданным условиям: F1-score 0.9, и пропуск ботов менее 3%. Собственно ее мы и будем использовать дальше.
    

2. Вторичные контесты
    - ***Максимально логичным образом обучить качественную модель, использующую для работы только 10 признаков из всего исходного множества.***
        * 1. Для выполнения данного пункта задания, будем использовать RandomForestClassifier, потому как на предыдущем задании, он показал лучший результат. 
        * 2. Определим топ-10 наиболее важных признаков, и на их основании создадим новый датасет (укороченный). Новый датасет, также как и в первом задании, разделим на тестовую и обучающую выборки в процентном соотношении 40 на 60 соответственно.
        * 3. После чего, модели были обучены и протестированы, на данных, которые были разделены на предыдущем шаге.
            * Для оценки моделей использовались следующие метрики:
                - Precision,  F1-score, confusion_matrix, а так же метрики из classification_report 
        * 4. В результате обучения на укороченном наборе признаков, заметилось улучшение качества модели, пропуск ботов снизился на 0,1%, а f мера осталась на уровне 0.99 

    - ***Обучить модель, обеспечивающую вероятность пропуска бота на уровне не выше 0.03, и имеющую насколько возможно низкую вероятность ложного обнаружения.***
        * 1. Продолжая апгрейд модели, произведем подбор гиперпараметров. Для подбора гиперпараметров, воспользуемся RandomizedSearchCV и BayesSearchCV. 
        * 2. При использовании RandomizedSearchCV произошло ухудшение качества модели, однако, модель удовлетворяет условиям лабораторной работы.
        * 3. При использовании BayesSearchCV модель показала лучший результат, по параметру пропуска ботов 1,3%, а f-score на уровне = 0,99.

# Итоги

В результате выполнения лабораторной работы, была получена относительно качественная модель.