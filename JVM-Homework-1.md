# Задача "Понимание JVM"

![image](https://user-images.githubusercontent.com/77538624/173370317-d834fae0-0dc3-4983-83f9-2df5540823f2.png)




**1.** *В Metaspace загружается класс JvmComprehension.* Создается фрейм main() в стеке, в нем создается переменная int i;

**2.** *В Metaspace загружается класс Object.* 
Создается переменная o типа Object, и в нее кладется ссылка на объект Object, который создается в heap;

**3.** *В Metaspace загружается класс Integer*. 
Создается переменная ii и объект типа Integer (ссылка на Integer ii в heap).

**4.** Вызывается метод printAll(), а значит создается новый фрейм. 
В этом фрейме создается переменная int i = 1 , а также передаются ссылки на объекты o и  ii.

**5.** Создается переменная типа Integer uselessVar в стеке и ссылка на объект Integer в heap.

**6.** *В Metaspace загружается класс System.* 
Вызывается метод println() объекта out класса System. В этот метод передаются ссылки на объекты o и ii, а также переменная i.

После выполнения println() удаляется фрейм System.out.println() в стеке, переменная i, и ссылки из данного фрейма на объекты ii и o в heap. 
Далее после выполнения метод PrintAll() удаляется его фрейм из стека, переменная i,  ссылки из него на объекты o и ii,  а также на Integer uselessVar. 
UselessVar зачищается сборщиком мусора.

**7.** Снова вызывается метод println() Объекта out класса System. В консоль выводится "finished".

После завершения метода main() удаляются ссылки из него на объекты o и ii, переменная i. Сборщик мусора удаляет объекты o и ii в heap.

