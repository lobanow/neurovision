# neurovision
Что решалось
Привести изображение к виду схожему с задаными условиями

 ![image](https://github.com/lobanow/neurovision/assets/71119059/12428b55-5f19-4e93-864f-83b985d59b8e)

Как решалось
Приводим матрицу заполненную 0 к заданному виду. Для этого создается агент, который может в одну единицу времени, переместится на одну из соседних клеток, при перемещении на клетку ее счетчик увеличивается на единицу. Клетка выбирается таким образом, чтобы минимизировать различие между текущей матрицей и эталонной. Для этого перед перемещением рассчитывается значение функции ошибок для текущей ячейки

K=∑max(0,n- ̃N/N)            N= ∑            ̃N=∑ ̃n     
Далее для каждой ячейки рассчитывается пробное значение ошибок:	

K=K0-∑max(0, ̃n- ̃N/N) +∑max(0, ̃n- ̃N/N*[n_xy+ 1])            
После этого агент переходит на клетку с минимальной функцией ошибок.
Как производилась параллелизация
При помощи multiprocessing создается несколько воркеров, а для того, чтобы они не конфликтовали используется lock

![image](https://github.com/lobanow/neurovision/assets/71119059/a5b5f707-372e-44f8-a0dc-2942ee5d946d)
