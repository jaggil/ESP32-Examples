> Códigos de ejemplo de los tutoriales de www.luisllamas.es
>
> Enlace entrada: https://www.luisllamas.es/esp32-i2c/
>
> Todo el contenido distribuido bajo licencia CCC, salvo indicación expresa


## El bus I2C en el ESP32
```cpp
void setup() {
  // Iniciar comunicación I2C
  Wire.begin();
}
```

```cpp
Wire.begin(I2C_SDA, I2C_SCL);
```



## Enviar Datos
```cpp
byte dataToSend = 0x42;  // Datos a enviar
byte slaveAddress = 0x50;  // Dirección del dispositivo esclavo

Wire.beginTransmission(slaveAddress);  // Iniciar transmisión al dispositivo
Wire.write(dataToSend);  // Enviar datos
Wire.endTransmission();  // Finalizar transmisión
```



## Recibir Datos
```cpp
byte receivedData;
int bytesToRead = 1;  // Cantidad de bytes a leer

Wire.requestFrom(slaveAddress, bytesToRead);  // Solicitar datos al dispositivo
if (Wire.available()) {
  receivedData = Wire.read();  // Leer datos recibidos
}
```



## Usando múltiples bus I2C en el ESp32
```cpp
#include <Wire.h>

// reemplazar por los pines que queráis usar
const int SDA_1 = 0;
const int SCL_1 = 0;
const int SDA_2 = 0;
const int SCL_2 = 0;

TwoWire MyI2C_1 = TwoWire(0);
TwoWire MyI2C_2 = TwoWire(1);

void setup() {
  MyI2C_1.begin(SDA_1, SCL_1, freq1);
  MyI2C_2.begin(SDA_2, SCL_2, freq2); 
}

void loop()
{
  delay(1000);  // do nothing
}
```


