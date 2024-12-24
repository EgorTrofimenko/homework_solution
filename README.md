# Лабораторная работа 6

1. Я Создал файл data.txt с произвольным содержимым при помощи команды:
```
echo -e "user1,25,developer\nuser2,30,designer\nuser3,22,manager\nuser4,35,developer\nuser5,29,developer" > data.txt
```
![image](https://github.com/user-attachments/assets/b488f484-2baa-48e3-a686-7d65971c1351)

2. Нашел все строки, содержащие слово "developer" и сохранил их в файл developers.txt:
```
grep "developer" data.txt > developers.txt
```
![image](https://github.com/user-attachments/assets/43965ac7-3ba5-4361-b0c9-d8dc89dcf28c)

3. Нашел средний возраст пользователей из developers.txt:
![image](https://github.com/user-attachments/assets/6243cc68-c8da-4ded-92cf-8aa0fcbd3a15)

4. Создал скрипт error_filter.sh, который будет проверять существование файла и выводить ошибку или содержимое:
![image](https://github.com/user-attachments/assets/5c5c35b0-9a60-4c37-872c-dbe84dfd48ef)
сделал его исполнимым:
```
 chmod +x error_filter.sh
```
Теперь, если файл существуте, выполняя данный скрипт, я получаю строки, содержащие искомое слово, в противном случае - ошибку
![image](https://github.com/user-attachments/assets/84e297d6-57df-46a1-b3c0-5c70dd5ff0e5)
5. Перенаправил поток вывода в отдельные файлы 
```
./error_filter.sh data.txt developer > output.log 2> error.log
```
![image](https://github.com/user-attachments/assets/279e6a6e-b40d-47dd-9168-eb2d32e7c48d)

6. Отсортировал пользователей по возрасту в порядке убывания
```
sort -t ',' -k2,2nr developers.txt > sorted_developers.txt
```
![image](https://github.com/user-attachments/assets/dae070cc-7c65-46ba-95d4-33cca55ff5f0)

Удалил строки с дублирующимися именами и вывел в файл unique_sorted.txt
```
sort -t ',' -k2,2nr developers.txt | uniq > unique_sorted.txt
```
7. Создал конвейер для подсчета строк и сохранил результат в role_counts.txt
```
echo "developer: $(grep -c "developer" data.txt)" > role_counts.txt
echo "manager: $(grep -c "manager" data.txt)" >> role_counts.txt
echo "designer: $(grep -c "designer" data.txt)" >> role_counts.txt
```
![image](https://github.com/user-attachments/assets/e993da9c-d4e4-4bf9-9cd0-9a5f956b8a27)
