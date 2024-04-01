# ДЗ №3

#### Даняев Артем Андреевич

## Результаты работы
  ### Projection of real images
  Сначала находим вектор с помощью модели Encoder4Editing, затем дополнительно улучшаем его с помощью оптимизации лоссов Lpips_loss, Reg_loss, Rec_loss
  
  ![image](https://github.com/adanyaev/itmo-deep-gen-models/assets/38013055/61f6d558-ff41-46e2-8990-b0770f270dc0)

  ### Style transfer
  Применим Styles crossover для добавления стилей к лицам актеров
   #### Стиль 1
   ![image](https://github.com/adanyaev/itmo-deep-gen-models/assets/38013055/613ca2e0-c921-40d7-b94b-2736863aeccd)
   ![image](https://github.com/adanyaev/itmo-deep-gen-models/assets/38013055/fb7ad2d6-62a7-4d62-a8bb-8b9bfa28a2c7)
   #### Стиль 2
   ![image](https://github.com/adanyaev/itmo-deep-gen-models/assets/38013055/3ce28e8a-6f79-4ed6-a940-d3f34f22d90b)
   ![image](https://github.com/adanyaev/itmo-deep-gen-models/assets/38013055/c26b061d-d2eb-4776-8f6e-cd0cef19d52c)
   #### Стиль 3
   ![image](https://github.com/adanyaev/itmo-deep-gen-models/assets/38013055/9374adde-6ea3-4ca5-b253-8e0ce98c5fd7)
   ![image](https://github.com/adanyaev/itmo-deep-gen-models/assets/38013055/e600d9d8-45ac-42f3-afa0-db928931256b)

  ### Expression transfer
  Применим интерполяцию для редакцирования лиц актеров
  
   * Возраст
     
      ![image](https://github.com/adanyaev/itmo-deep-gen-models/assets/38013055/7fb5d813-6047-4d42-a802-8854240f5e31)

   * Положение лица

      ![image](https://github.com/adanyaev/itmo-deep-gen-models/assets/38013055/cafc193e-f8d8-4ddc-87cf-3ea249c437be)

   * Улыбка

      ![image](https://github.com/adanyaev/itmo-deep-gen-models/assets/38013055/0ccacc87-ee74-43f2-8765-e1d22b56464a)

   * Злость

      ![image](https://github.com/adanyaev/itmo-deep-gen-models/assets/38013055/816acf5e-7ab6-4b64-b576-f57ad05bac46)
      ![image](https://github.com/adanyaev/itmo-deep-gen-models/assets/38013055/914cd2ae-40b6-4437-9626-2c42dfe8717e)
      ![image](https://github.com/adanyaev/itmo-deep-gen-models/assets/38013055/c67b5232-8ed1-47b9-8b8d-67545d8dca9d)
     
  ### Face swap
   
  Замена лица с помощью arcface loss. В ходе экспериментов подбирал оптимальные коэффициенты лоссов

  По строкам - изначальные лица, по столбцам - накладываемые лица

  ![image](swap_collage.png)








   






  



