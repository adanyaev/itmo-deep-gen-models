# ДЗ № 4

#### Даняев Артем Андреевич

## Результаты обучения

Все сгенерированные изображения (по 4 изображения для каждого из 5 зафиксированных для сравнения промптов для всех экспериментов) находятся в папке ./gen_images

Для обучения модели собрал датасет из 18 изображений с Уолтером Вайтом из сериала Breaking Bad

### Обучение StableDiffusion 1.5 методом Dreambooth

![img](gen_images/dreambooth_v1/street.jpg)

После обучения методом Dreambooth получаем генерации достаточно хорошего качества

### Обучение Stable Diffusion методом Dreambooth Lora
   #### lr=2e-6 rank=4
   
  ![img](gen_images/dreambooth_lora_k4_lr_2e_6/street.jpg)
  
  Можно заметить, что с дефолтными параметрами модель практически не обучилась под выбранного персонажа. Попробуем постепенно увеличивать learning rate.
  
  #### lr=2e-5 rank=4
  ![img](gen_images/dreambooth_lora_k4_lr_2e_5/street.jpg)

  #### lr=2e-4 rank=4
  ![img](gen_images/dreambooth_lora_k4_lr_2e_4/street.jpg)

  #### lr=2e-3 rank=4
  ![img](gen_images/dreambooth_lora_k4_lr_2e_3/street.jpg)

  Как можно увидеть, с learning rate = 2e-3 модель уже слишком сильно переобучилось, оптимальное качество генерации было достигнуто при learning rate = 2e-4, зафиксируем его и проведем эксперименты с параметром rank.

  #### lr=2e-4 rank=8
  ![img](gen_images/dreambooth_lora_k8_lr_2e_4/street.jpg)

  После увеличения rank до 8, качество генерации визуально ухудшилось. Попробуем уменьшить rank до 2

  #### lr=2e-4 rank=2
  ![img](gen_images/dreambooth_lora_k2_lr_2e_4/street.jpg)

  С уменьшенным rank = 2 качество генерации также ухудшилось, таким образом, лучшие результаты были достигнуты с параметрами learning rate = 2e-4  и rank = 4

  Сравнивая результаты Dreambooth и Lora Dreambooth, можно сказать, что качество генерации немного лучше у Dreambooth, что и следовало ожидать.

### Controlnet Canny-edge

  Выбранные референсные изображения:
  
  ![controlnet2_lenin](https://github.com/adanyaev/itmo-deep-gen-models/assets/38013055/bcfa4ef8-7d28-4cda-a297-2ce8f109eae3)

  ![controlnet_dost](https://github.com/adanyaev/itmo-deep-gen-models/assets/38013055/a5133fe1-7e2a-4987-a5b5-e3539c76bcfe)

  #### Результаты Dreambooth c Controlnet Canny-edge

  ![image](https://github.com/adanyaev/itmo-deep-gen-models/assets/38013055/f7259ccc-11b7-46be-8dc2-586779f3c974)

  ![image](https://github.com/adanyaev/itmo-deep-gen-models/assets/38013055/0e427356-0d8e-4521-816e-053c44f512c9)

  #### Результаты лучшего эксперимента Dreambooth Lora c Controlnet Canny-edge

  ![image](https://github.com/adanyaev/itmo-deep-gen-models/assets/38013055/d4fec09f-bd17-4bf8-a0de-cb6a86e0fcd2)

  ![image](https://github.com/adanyaev/itmo-deep-gen-models/assets/38013055/bcbbeb11-d020-4bc2-bcac-27bdb86cc839)





  
