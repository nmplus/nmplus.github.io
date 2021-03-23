# Shell 간단 정리

변수 

변수 선언 

타입 추론을 한다. 

val=10 
echo $val      
#10 
 

str="hello world" 
echo $str      
#hello world 
 

arr=("value1 value2 value3") 
echo $arr      
#value1 value2 value3 
 

스크립트 인자 전달 

./example01.sh Hello world 

echo "this file : $0"       #this file : ./example01.sh 
echo "argument size : $#"   #argument size : 2 
echo "Process ID : $$"      #Process ID : 10062 
echo "arguments : $*"       #arguments : Hello world 
echo "argument 1 : $1"      #argument 1 : Hello 
echo "argument 2 : $2"      #argument 2 : world 
 

if 

문자열 비교 

문자는 = 로 비교를 한다 

if [[  $str = "str" ]]; then 
  echo "str equels str" 
fi 
#str equels str 
 

문자가 같지 않을때 

if [[ $str != $str1 ]]; then 
  echo "str diff str1" 
fi 
#str diff str1 
 

빈 문자가 아닌때 

if [[ -n $str ]]; then 
  echo "is not null" 
fi 
#is not null 
 

빈 문자열 일때 

if [[ -z $str2 ]]; then 
  echo "is null" 
fi 
#is null 
 

숫자 비교 

같은 숫자인지 비교 

if [[ i -eq 1 ]]; then 
  echo "i=1" 
fi 
#i=1 
 

다른 숫자인지 비교 

if [[ i -ne 2 ]]; then 
  echo "i!=1" 
fi 
#i!=1 
 

i > j 라면 참 

if [[ 2 -gt i ]]; then 
  echo "2 > i" 
fi 
#2 > i 
 

i >= j 라면 참 

if [[ 1 -ge i ]]; then 
  echo "1 >= i" 
fi 
#1 >= i 
 

if [[ 2 -ge i ]]; then 
  echo "2 >= i" 
fi 
#2 >= i 
 

i < j 라면 참 

if [[ i -lt 2 ]]; then 
  echo "i < 2" 
fi 
#i < 2 
 

i <= j 라면 참 

if [[ i -le 2 ]]; then 
  echo "i <= 2" 
fi 
#i <= 2 
 

if [[ i -le 1 ]]; then 
  echo "i <= 1" 
fi 
#i <= 1 
 

파일 

-e 해당 파일이 존재 하면 참(폴더도 가능?) 

-f 해당 파일이 존재 하면 참 

-d 해당 디렉토리 존재 하면참 

if [[ -e example01.sh ]]; then 
  echo "found example01.sh" 
fi 
#found example01.sh 
 

if [[ -f example01.sh ]]; then 
  echo "found example01.sh" 
fi 
#found example01.sh 
 

if [[ -d example02 ]]; then 
  echo "found example02 dir" 
fi 
#found example02 dir 
 

if elif else 

if [[ -f example02 ]]; then 
  echo "example01 dir?" 
elif [[ -d example02 ]]; then 
  echo "example02 dir" 
else 
  echo "not found example02" 
fi 
#example02 dir 
 

and or 

if [[ -d example02 && -f example02.sh ]]; then 
  echo "example02 dir and example02.sh file" 
fi 
#example02 dir and example02.sh file 
 

if [[ -f example02 || -f example02.sh ]]; then 
  echo "example02 file or example02.sh file" 
fi 
#example02 file or example02.sh file 
 

for , while 

arr=("value1 value2 value3 value4 value5") 
 

forin 

for value in ${arr}; do 
  echo "$value" 
done 
#value1 
#value2 
#value3 
#value4 
#value5 
 

for file in $(ls -a | grep example) 
do 
    echo "$file" 
done 
#example01.sh 
#example02 
#example02.sh 
#example03.sh 
#example04.sh 
 

while 

i=0 
while [ $i -lt 5 ] 
do 
  echo $i 
#((i++)) 
let "i++" 
done 
#0 
#1 
#2 
#3 
#4 
 

password example 

i=0 
echo "Enter Password : " 
read password1 
 

echo "Retype Password : " 
read password2 
 

while [[ $password1 != $password2 && $i -lt 2 ]]; do 
  echo "Password mismatch Try again" 
  echo "Retype Password : " 
  read password2 
  ((i++)) 
done 
if [[ $password1 != $password2 ]]; then 
  echo "Retry password" 
else 
  echo "OK password" 
fi 
 

#Enter Password :  
#hello123 
#Retype Password :  
#hello12 
#Password mismatch Try again 
#Retype Password :  
#hello123 
#OK password 
 

function 

function 이란 키워드를 안써도 되긴하다. 하지만 가독성이 떨어지므로 쓰기로하겠다. 

함수 호출. 간단하다. 

function func(){ 
  echo "i am function" 
} 
func 
#i am function 
 

파라미터 전달 

function funcParam(){ 
  echo "param Count : $#" 
  echo "param #1 : $1" 
  echo "param #2 : $2" 
} 
#param Count : 2 
#param #1 : Hello 
#param #2 : world 
funcParam Hello world 
 

return string 

function funcReturnStr(){ 
  val="i love programming" 
  echo "$val" 
} 
retval=$(funcReturnStr) 
echo $retval            #여기에서 출력이 된다. 여기를 지우면 출력되지 않는다. 
#i love programming 
 

return number 

function funcReturnInt(){ 
  val=5 
  return $val 
} 
funcReturnInt 
ret=$? 
echo $ret 
#5 
 

return array (string 동일한 방식) 

function funcReturnArr(){ 
  arr=(1 2 3 4 5) 
  # echo ${arr[@]} 
  echo ${arr[*]} 
} 
 

retArr=$(funcReturnArr) 
echo $retArr 
#1 2 3 4 5 