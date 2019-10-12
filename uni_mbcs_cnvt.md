__unicode > multibyte__
```cpp
wchar_t strUnicode[256] = {0,};
char    strMultibyte[256] = {0,};
wcscpy_s(strUnicode,256,L"유니코드");
int len = WideCharToMultiByte( CP_ACP, 0, strUnicode, -1, NULL, 0, NULL, NULL );    
WideCharToMultiByte( CP_ACP, 0, strUnicode, -1, strMultibyte, len, NULL, NULL );
```

multibyte > unicode
``` cpp
wchar_t strUnicode[256] = {0,};
char    strMultibyte[256] = {0,};
strcpy_s(strMultibyte,256,"멀티바이트");
int nLen = MultiByteToWideChar(CP_ACP, 0, strMultibyte, strlen(strMultibyte), NULL, NULL);
MultiByteToWideChar(CP_ACP, 0, strMultibyte, strlen(strMultibyte), strUnicode, nLen);
```

unicode > utf8
``` cpp
wchar_t strUni[256] =L"유니코드";
char strUtf8[256] ={0,};
int nLen = WideCharToMultiByte(CP_UTF8, 0, strUni, lstrlenW(strUni), NULL, 0, NULL, NULL);
WideCharToMultiByte (CP_UTF8, 0, strUni, lstrlenW(strUni), strUtf8, nLen, NULL, NULL);
```

utf8 > unicode
``` cpp
wchar_t strUnicode[256] = {0,};
char    strUTF8[256] = {0,};
strcpy_s(strUTF8,256,"utf-8글자..");
int nLen = MultiByteToWideChar(CP_UTF8, 0, strUTF8, strlen(strUTF8), NULL, NULL);
MultiByteToWideChar(CP_UTF8, 0, strUTF8, strlen(strUTF8), strUnicode, nLen);
```



**1) Unicode to MBCS**

``` cpp
char* ConvertUnicodeToMultybyte(CString strUnicode)
{
    int nLen = WideCharToMultiByte(CP_ACP, 0, strUnicode, -1, NULL, 0, NULL, NULL);

    char* pMultibyte  = new char[nLen];
    memset(pMultibyte, 0x00, (nLen)*sizeof(char));

    WideCharToMultiByte(CP_ACP, 0, strUnicode, -1, pMultibyte, nLen, NULL, NULL);

    return pMultibyte;
}
```

**2) MBCS to Unicode**
``` cpp
CString ConvertMultibyteToUnicode(char* pMultibyte)
{
    int nLen = strlen(pMultibyte);

    WCHAR *pWideChar = new WCHAR[nLen];
    memset(pWideChar, 0x00, (nLen)*sizeof(WCHAR));

    MultiByteToWideChar(CP_ACP, 0, (LPCSTR)pMultibyte, -1, pWideChar, nLen);

    CString strUnicode;
    strUnicode.Format(_T("%s"), pWideChar);

    delete [] pWideChar;

    return strUnicode;
}
```

**3) Usage**

```
CString strUnicode(_T("유니코드"));
char* pMultibyte = ConvertUnicodeToMultibyte(strUnicode);

char* pMultibyte = "멀티바이트";
CString strUnicode = ConvertMultibyteToUnicode(pMultibyte);
```
