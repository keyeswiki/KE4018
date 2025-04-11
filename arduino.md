# Arduino


## 1. Arduino简介  

Arduino是一款广泛使用的开源电子原型平台，旨在通过易于使用的硬件和软件，帮助用户创建互动项目。Arduino硬件通常基于微控制器，用户可以通过Arduino IDE编程，使用C/C++语言来控制多种传感器、马达和其他电子元件。Arduino的优点在于其友好的开发环境以及强大的社区支持，使得初学者和专业开发者都能够轻松上手。Arduino适用于教育、原型开发、产品设计和个人创作等多个领域，促进了物联网和创客文化的发展。  

## 2. 连接图  

![](media/408ee02811c409060407906f87d444ec.png)  

## 3. 测试代码  

```cpp  
byte sensorPin = 3; // 定义数字口3  
byte indicator = 13; // 定义数字口13  

void setup() {  
    pinMode(sensorPin, INPUT); // 设置数字口3位输入  
    pinMode(indicator, OUTPUT); // 设置数字口13为输出  
    Serial.begin(9600); // 设置波特率  
}  

void loop() {  
    byte state = digitalRead(sensorPin); // 读取到数字口3的数值赋值给state  
    digitalWrite(indicator, state); // 控制数字口13的状态  

    if (state == 1) { // 当数值口3位高电平时  
        Serial.println("Somebody is in this area!"); // 串口监视器输出  
    } else if (state == 0) { // 当数值口3位低电平时  
        Serial.println("No one!"); // 串口监视器输出  
    }  
    delay(500); // 延迟0.5S  
}  
```  

## 4. 测试结果  

烧录好测试代码，按照接线图连接好线，通过USB供电后，打开串口监视器并设置波特率为9600。当检测到人体运动时，Plus板上D13的指示灯亮起，串口监视器中显示"Somebody is in this area!"；没有检测到人体运动时，Plus板上D13的指示灯熄灭，串口监视器中显示"No one!"。


