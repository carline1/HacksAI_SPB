Есть 2 файла: 
неназванный - тест на валидационной выборке, мы мерели precisidion, recall
Второй файл отображает наше намерение, с таким обучением точность должна упасть, но настоящая точность(тест на онлайне) будет выше. Почему? 
Во первых если у нас будет новый бользователь ALS не поможет, нужна история. Мы использовали MiniBatchKMeans для обучения на сэмплах по 0,05 датасета(у нас слабые компы)
На их основе мы подбираем самые поппулярные товары по кластерам
Во вторых в овсех случаях добавляем немного случайных товаров в историю и топ у ближайших к нашему кластеру тоже.
В третьих к пользователям у которых есть история мы несколько изменяем веса в sparse матрицах на ALS: берём случайные товары с топа по кластерам и умножаем на некоторый коэффициент
(Этот коэффициент вы тоже можете покрутить и посмотреть на точность), увеличиваем случайнные коэффициенты на тоже некоторый коэффициент.
Топ рекомендаций мы считаем по формуле: вероятность "покупки в магазине" * "средний чек по этому магазину у кластера нашего пользователя.
