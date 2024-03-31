# ДЗ №2
### Даняев Артем Андреевич

Выбранный для обучения DCGAN датасет: [Celeba](https://mmlab.ie.cuhk.edu.hk/projects/CelebA.html) (Align&Cropped Images)

Tensorboard логи обучения находятся в папке `./logs_dcgan`

## Результаты обучения
 1. Эксперимент 1
    
  Генератор на CSPup блоках. Добавил к изначальной имплементации дискриминатора дополнительный блок свертки для работы с изображениями 128x128.

  В зоде эксперимента подбирал оптимальный learning rate и batch size для генератора и дискриминатора, чтобы добиться более-менее стабильной тренировки. 
  Остановился на значениях lr_g = 0.0001, lr_d = 0.00005, batch_size = 64, но хороших результатов достичь не получилось, т.к. дискриминатор всегда обучался слишком быстро, его лосс стремительно падал, и генератор за ним не успевал.
  ![image](https://github.com/adanyaev/itmo-deep-gen-models/assets/38013055/27e711e5-86d7-4b7a-84fe-237211320907)
  ![image](https://github.com/adanyaev/itmo-deep-gen-models/assets/38013055/a8f6f98c-19e5-44c3-b6c7-87d30bb0459f)
  
 2. Эксперимент 2
    
    Попроовал применить [фишку](https://github.com/soumith/ganhacks/issues/36) из репозитория gan-hacks, чтобы побороться со слишком быстрым уменьшением лосса дискриминатора, заменив BCELoss на BCEWithLogitsLoss, и, соответственно, убрав сигмоиду в конце         дискриминатора
    
    ![image](https://github.com/adanyaev/itmo-deep-gen-models/assets/38013055/6be3cab6-523b-483f-8ce0-9252afe5d3a7)
    ![image](https://github.com/adanyaev/itmo-deep-gen-models/assets/38013055/d0d8aebc-dd51-4605-8217-593c9db275df)

    Как можно заметить, значительного улучшения данная модификация не дала
 3. Эксперимент 3

    Попробовал обучать дискриминатор каждые n итераций. Я тестировал разные n, лучшие результаты получились при n=2
    ![image](https://github.com/adanyaev/itmo-deep-gen-models/assets/38013055/a0b71306-37fc-4946-a92a-e5aa5fd638a5)
    ![image](https://github.com/adanyaev/itmo-deep-gen-models/assets/38013055/363b7282-11ca-414e-bc09-3c93ffd7822b)

    Данная модификация значительно дестабилизировала обучение и привела к mode collapse

 4. Эксперимент 4

    Попробовал уменьшить количество сверток в дискриминаторе, заменив один из слоев на AvgPool2d. Меньшая по размеру модель должна быть менее подвержена переобучению.

    ![image](https://github.com/adanyaev/itmo-deep-gen-models/assets/38013055/4f75a646-817b-4ad6-840c-e5016bd19746)
    ![image](https://github.com/adanyaev/itmo-deep-gen-models/assets/38013055/9b9a3c11-bdd0-4584-9740-220193ed5d51)

    Применение данной модификации позволило улучшить сходимость, лосс дискриминатора перестал опускаться до околонулевых значений, и, судя по графикам, тренировка проходила намного стабильнее. Будем использовать данную модификацию и в дальнейших         
    экспериментах.

  5. Эксперимент 5

      Попробовал модифицировать архитектуру генератора, добавив BatchNorm2d в блок CSPup.
      ![image](https://github.com/adanyaev/itmo-deep-gen-models/assets/38013055/8f25ce39-ecfe-4db6-92a5-b654f36e51f1)
      ![image](https://github.com/adanyaev/itmo-deep-gen-models/assets/38013055/20812ddb-479f-43e4-ae91-61dea11a9c4c)


  6. Эксперимент 6

       Попробовал модифицировать архитектуру генератора, заменив функции активации в блоке CSPup на LeakyReLU
      ![image](https://github.com/adanyaev/itmo-deep-gen-models/assets/38013055/9f6b5641-3f11-49cc-91dc-114877663805)
      ![image](https://github.com/adanyaev/itmo-deep-gen-models/assets/38013055/f4c1174a-f17a-46e4-b757-a12a78328f9e)


     Применение BatchNorm и LeakyRELu в генераторе в целом ощутимо улучшило качество генерируемых картинок.








