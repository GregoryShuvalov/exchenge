- **echo $PATH** - просмотр путей
- **xport PATH=$PATH://home/moon** - пример добавления записи в PATH

- **ls -la /path/file** - посмотреть права доступа к файлу скирпта - [[Linux#Работа с файлами]]
- **cmod +x /path/file** - сделать файл исполняемым [[Linux#Права доступа к файлам/каталогам]]

- **which name** - найти месторасположение скрипта(необходимо предварительно убрать расширение '.sh')

- **read -p "Enter:" task_name** - Ввод строки для переменой скрипта

  **echo $CODE | cut -d '_' -f $character** - Выбрать символ из строки без учета "_"

  **expr 5 + 2**  - арифметические операции 
  $(($1 + $2))

опрераторы сравнения 
if then fi
= str
!= str
-eq число слева не равно числу справа
-ne наоборот
-gt слева больше чем справа
-lt слева меньше чем справа

-e проверяет, существует ли файл.
-d выясняет, является ли указанный путь каталогом.Оператор -s удостоверяется, имеет ли файл размер больше нуля.
-x делает проверку, является ли файл исполняемым. 
-w узнает, доступен ли файл для записи.
Также очень часто используются операторы для проверки параметров.
-z проверяет, существует ли строка.
-d-n делает тоже самое, но инвертирует ответ.
Иногда ты можешь встретиться вот с такой командой `test`.


string1_length=${#string1}  - длина строки


ПРИМЕР
 Если один из параметров не задан, скрипт должен выйти с сообщением Zero length. Используй команду exit для выхода.

Скрипт должен сравнить длину строк, если первая строка длинее, то написать String 1 is longer, если вторая то String 2 is longer и Strings are the same length, если они равны

Скрипт должен сравнить содержимое строк, если они одинаковые, то написать Strings have the same content, а если они не равны, то Strings are not the same

	tring1=$1
	string2=$2
	
	if [ -z $string1 ] || [ -z $string2 ]
	then
	  echo "Zero length"
	  exit
	fi
	
	string1_length=${#string1}
	string2_length=${#string2}
	
	if [ $string1_length -gt $string2_length ]
	then
	  echo "String 1 is longer"
	elif [ "$string2_length" -gt "$string1_length" ]
	then
	  echo "String 2 is longer"
	else
	  echo "Strings are the same length"
	fi
	
	if [ "$string1" == "$string2" ]
	then
	  echo "Strings have the same content"
	else
	  echo "Strings are not the same"
	fi

ПРИМЕР определить месяц
if [ -z $1 ]
then
  echo "No month number"
  exit
fi

if [ $1 -gt 12 ] || [ $1 -lt 1 ]
then
  echo "Invalid month number"
else
    arr=(go
    January
    February
    March
    April
    May
    June
    July
    August
    September
    October
    November
    December)

    echo ${arr[$1]}
  exit
fi


ЦИКЛЫ
for task in $(cat all-task.txt)
		 1 2 3 4 5
		 {0..15}	
do
  skript $task
done

