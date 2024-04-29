## Профильное задание на стажировку VK ##
### Инженер машинного обучения ###

Обучена модель XGBRanker

**NDCG@5: 0.9576**

*посчитанно на ~20% данных (в тест отобрано 20% поисковых запросов)*

### Работа представлена в трех jupyet notebook. ###

1. **EDA.ipynd** - содержит описание работы по анализу данных;
2. **base_model.ipynd** - содержит выбор модели, перед подбором гиперпараметров;
3. **Optuna.ipynb** - содержит процесс подбора гиперпараметров и измерение финальной метрики качества.

### Краткое описание процесса обучения модели. ###

Довольно сложно работать с неизвестными признаками, тем более, представленными в таком количестве. Хотя, возникло ощущение, что они сгенерированы, уменьшение признакового пространство очень сильно ухудшило качество. В связи с тем, что градиентный бустинг довольно мощный инструмент и представленное количество признаков не являлось запредельным, было решено избавиться только от совершенно неинформативных признаков. Как-то подготавливать данные тоже не стал из расчета, что деревьям это не сильно нужно. Разве что проблема большого количества выбросов волновала, но предположил, что данные на которых будет применяться модель будут схожими с обучающей выборкой.

После этого был выбор между CatBoost и XGBoost. Больше мне знаком первый (но не в задаче ранжирования) и, обычно, он очень хорошо показывал себя на стандартных настройках. В этот раз CatBoost, проиграл XGBoost'у. (upd: при перезапуске получился другой результат, не зафиксировал seed)
Далее, подбор гиперпараметров с помощью библиотеки optuna.
