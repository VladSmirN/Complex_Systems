## Запуск модели

Для запуска нужно запустить команду :

docker run --rm --gpus all -p 3000:3000 vladsmirn/car_detection:latest

Далее нужно перейти на http://localhost:3000/

Далее воспользоваться Swagger методом render для демонстрации работы модели 
![alt text](https://github.com/VladSmirN/Complex_Systems/blob/master/2024-11-02_11-46_1.png) 

[Описания bentoml сервиса](https://github.com/VladSmirN/Complex_Systems/tree/master/inference/ml)

## Подготовка данных 
Данные разделялись на train и valid, в valid попадало 30%

Учитывалось, что распределение количества машин на фото в train и valid одинаковое. Это достигалось при помощи параметра stratify в функции train_test_split 

В датасет не были включены 'ломаные' изображения

Далее из данных формировался yolo датасет 

Код с подготовкой данных:
[main.ipynb](https://github.com/VladSmirN/Complex_Systems/blob/master/main.ipynb)

## Обучение модели
Обучалась модель yolo11 

Метрики обучение:
![alt text](https://github.com/VladSmirN/Complex_Systems/blob/master/results.png) 

Код с запуском обучения(в конце)
[main.ipynb](https://github.com/VladSmirN/Complex_Systems/blob/master/main.ipynb)

## Повышение точности
Для представленного домена данных точность удолитворительная (map50 близок к 1.0) 
Для создания полноценного детектора автомобилий требуется расширения датасета (разные ракурсы, разные камеры, разные погодные условия, разные географические расположения )
