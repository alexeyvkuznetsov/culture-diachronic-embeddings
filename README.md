# Когда слово становится понятием?

Код и результаты к статье **«Когда слово становится понятием? Диахронические векторные модели в исследовании культуры (на материале британской прессы XIX века)»**. Статья подготовлена для XXXVI Международной научной конференции «Язык и культура» (2026).

В статье прослеживается, как английское слово *culture* превращается из термина земледелия в понятие. Материал — британская пресса 1800–1910-х годов. Ноутбук воспроизводит все числа, таблицу и рисунки статьи.

## Структура

```
analysis.ipynb                        расчёты, таблица и рисунки статьи
requirements.txt                      зависимости для локального запуска
results/
  numbers_in_article.txt              все числа, приведённые в тексте статьи
  shift_summary.csv                   общий сдвиг culture и контрольной группы (рис. 1)
  shift_all_words.csv                 общий сдвиг по каждому слову
  changepoints_pelt.csv               точки перелома PELT для culture и контрольных слов
  table1_neighbors.csv                табл. 1, ближайшие соседи culture
  neighbors_culture_top30.csv         30 соседей culture по всем десятилетиям
  fields_balance.csv                  баланс семантических полей и проверки устойчивости (рис. 2)
  relations.csv                       culture–cultivation, culture–civilisation
  neighbors_civilisation_top30.csv    30 соседей civilisation по всем десятилетиям
  fig1_shift_bw.png                   рис. 1, чёрно-белый, 300 dpi
  fig2_fields_bw.png                  рис. 2, чёрно-белый, 300 dpi
```

## Соответствие статьи и ноутбука

| В статье | Раздел ноутбука | Файл |
| --- | --- | --- |
| Общий сдвиг, рис. 1 | 4 | `shift_summary.csv`, `fig1_shift_bw.png` |
| Точки перелома | 4 | `changepoints_pelt.csv` |
| Ближайшие соседи, табл. 1 | 5 | `table1_neighbors.csv` |
| Баланс полей, рис. 2 | 6 | `fields_balance.csv`, `fig2_fields_bw.png` |
| *culture* и *civilisation* | 7 | `relations.csv`, `neighbors_civilisation_top30.csv` |
| Все числа в тексте | 9 | `numbers_in_article.txt` |

## Запуск

**Google Colab.** Откройте `analysis.ipynb` и выполните все ячейки по порядку. Недостающие библиотеки установятся автоматически. Модели загрузятся в `/content/lwm_vectors`.

**Локально.** Нужен Python 3.10 или новее и около 4 ГБ свободной памяти.

```bash
pip install -r requirements.txt
jupyter nbconvert --to notebook --execute --inplace analysis.ipynb
```

Каталоги задаются переменными окружения. `LWM_MODEL_DIR` указывает, куда скачивать модели (по умолчанию `models/`). `RESULTS_DIR` указывает, куда сохранять результаты (по умолчанию `results/`).

Первый запуск скачивает около 1,6 ГБ и занимает 15–20 минут. Нужные векторы сохраняются в `results/cache.pkl`, поэтому повторные запуски занимают секунды.

## Данные

Используются опубликованные десятилетние модели проекта *Living with Machines*.

Pedrazzini N., McGillivray B. Diachronic word embeddings from 19th-century newspapers digitised by the British Library (1800–1919). Zenodo, 2022. DOI: [10.5281/zenodo.7181682](https://doi.org/10.5281/zenodo.7181682). Лицензия CC BY 4.0.

Параметры моделей: word2vec skip-gram, размерность 200, окно 3, 5 эпох. Модели всех десятилетий выровнены на пространство 1910-х ортогональным преобразованием Прокруста. Методическое описание дано в статье: Pedrazzini N., McGillivray B. Machines in the Media: Semantic Change in the Lexicon of Mechanization in 19th-Century British Newspapers // Proceedings of the 2nd International Workshop on Natural Language Processing for Digital Humanities. 2022. P. 85–95. DOI: 10.18653/v1/2022.nlp4dh-1.12.

Файлы моделей и промежуточный кэш в репозиторий не входят.

## Как цитировать

[И. О. Фамилия]. Когда слово становится понятием? Диахронические векторные модели в исследовании культуры (на материале британской прессы XIX века) // Язык и культура : сб. науч. тр. XXXVI Междунар. науч. конф. [город], 2026. [страницы]

## Лицензия

Код распространяется по лицензии MIT (см. `LICENSE`). Модели распространяются их авторами по лицензии CC BY 4.0.
