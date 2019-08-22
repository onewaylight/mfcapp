[Go To Main](readme.md)

# 레이저 다이오드의 기능 및 성능측정 자동화 Software
레이저 다이오드의 생산후 기능 및 성능측정 자동화 Tool입니다.

사용된 계측기는 다음과 같습니다.
* ILX LPA9070
* KEITHLEY Source Meter(2400)
* Anritsu OSA 9710C
* Agilent 86120B Wavelength meter
* ILX Lightwave LDT5948 Temperature Controller

Communication Protocol: GPIB, RS-232C
계측기와의 주요 통신은 GPIB 및 RS-232C로 통신을 합니다.
테스트 후 결과를 Excel File로 출력하며 그 정보를 모델에 
따라 DB화 하여 저장하도록 되어있습니다.

- Target OS: Windows 
- Tools : Visual Studio 2010
- Language : VC++/MFC

#### Screen #1 ####
![](images/Gui-c1.PNG)

#### Screen #2 ####
![](images/Gui-c2.PNG)

#### Screen #3 ####
![](images/Gui-c3.PNG)

#### Screen #4 ####
![](images/Gui-c4.PNG)

#### Screen #5 ####
![](images/Gui-c5.PNG)

#### Screen #6 - Excel Report ####
![](images/excelReport.PNG)

#### Screen #7 - Instruments Connection Diagram ####
![](images/LD-SigLine.png)
