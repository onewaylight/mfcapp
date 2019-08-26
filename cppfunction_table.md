# Thread Creation in C++11

https://thispointer.com//c-11-multithreading-part-1-three-different-ways-to-create-threads/

```
#include <thread>
```

1. Function Pointer
2. Function Objects
3. Lambda functions

```
std::thread thObj(<CALLBACK>);
```

# Creating a thread using Function Pointer
```
#include <iostream>
#include <thread>
 
void thread_function()
{
    for(int i = 0; i < 10000; i++);
        std::cout<<"thread function Executing"<<std::endl;
}
 
int main()  
{
    
    std::thread threadObj(thread_function);
    for(int i = 0; i < 10000; i++);
        std::cout<<"Display From MainThread"<<std::endl;
    threadObj.join();    
    std::cout<<"Exit of Main function"<<std::endl;
    return 0;
}
```

# Creating a thread using Function Objects
```
#include <iostream>
#include <thread>
class DisplayThread
{
public:
    void operator()()     
    {
        for(int i = 0; i < 10000; i++)
            std::cout<<"Display Thread Executing"<<std::endl;
    }
};
 
int main()  
{
    std::thread threadObj( (DisplayThread()) );
    for(int i = 0; i < 10000; i++)
        std::cout<<"Display From Main Thread "<<std::endl;
    std::cout<<"Waiting For Thread to complete"<<std::endl;
    threadObj.join();
    std::cout<<"Exiting from Main Thread"<<std::endl;
    return 0;
}
```

# Creating a thread using Lambda functions
```
#include <iostream>
#include <thread>
int main()  
{
    int x = 9;
    std::thread threadObj([]{
            for(int i = 0; i < 10000; i++)
                std::cout<<"Display Thread Executing"<<std::endl;
            });
            
    for(int i = 0; i < 10000; i++)
        std::cout<<"Display From Main Thread"<<std::endl;
        
    threadObj.join();
    std::cout<<"Exiting from Main Thread"<<std::endl;
    return 0;
}
```
```
#include <iostream>
#include <thread>
void thread_function()
{
    std::cout<<"Inside Thread :: ID  = "<<std::this_thread::get_id()<<std::endl;    
}
int main()  
{
    std::thread threadObj1(thread_function);
    std::thread threadObj2(thread_function);
 
    if(threadObj1.get_id() != threadObj2.get_id())
        std::cout<<"Both Threads have different IDs"<<std::endl;
 
        std::cout<<"From Main Thread :: ID of Thread 1 = "<<threadObj1.get_id()<<std::endl;    
    std::cout<<"From Main Thread :: ID of Thread 2 = "<<threadObj2.get_id()<<std::endl;    
 
    threadObj1.join();    
    threadObj2.join();    
    return 0;
}
```

# Function Quick Reference 
### Convert legacy code to support Unicode and _MBCS

Function |_UNICODE  | TCHAR     | Description
---------|----------|-----------|-------------------------
strcpy   | wcscpy   | _tcscpy   | (문자열을 복사) 
strncpy  | wcsncpy  | _tcsncpy  | ( 사이즈 만큼 복사) 
strlen   | wcslen   | _tcslen   | (문자열 길이 확인)  
strcat   | wcscat   | _tcscat   | (두 문자열 이어 붙이기) 
strncat  | wcsncat  | _tcsncat  | (사이즈 만큼 이어 붙이기) 
strcmp   | wcscmp   | _tcscmp   | (문자열 비교) (반환 값(-1, 0, 1)) 
strncmp  | wcsncmp? | _tcsncmp  | (사이즈 만큼 문자열 비교) 
stricmp  | wcsicmp  | _tcsicmp  | (대소문자를 구별하지 않고 문자열을 비교) 
strnicmp | wcsnicmp | _tcsnicmp | (사이즈 만큼 대소문자를 구별하지 않고 문자열을 비교)
strchr   | wcschr   | _tcschr   | (문자 찾기) 
strrchr  | wcsrchr  | _tcsrchr  | (문자 찾기 (문자열 끝에서 부터 검색)) 
strstr   | wcsstr   | _tcsstr   | (문자열 찾기)
strpbrk  | wcspbrk  | _tcspbrk  | (문자 찾기 (두번째 인수를 찾고자 하는 문자들의 집합(문자열)으로 구성)   
strtok   | wcstok   | _tcstok   | (문자열 자르기 (두번째 인수를 집합(문자열)으로 구성 가능)) => 해당 문자가 NULL로 치환 됨
strset   | wcsset   | _tcsset   | (문자 치환, 첫째 인수의 모든 문자를 두번째 인수 문자로 변경함) => "abc" -> "bbb" 
strnset  | wcsnset  | _tscnset  | (사이즈 만큼 문자 치환) 
strupr   | wcsupr   | _tcsupr   | (대문자로 치환)
strlwr   | wcslwr   | _tcslwr   | (소문자로 치환) 
strrev   | wcsrev   | _tcsrev   | (문자열 역정렬) => "가나다라마" -> "마라다나가"
atoi     |          | _tstoi    |
atof     |          | _tstof    |
