# Primer parcial
![Tinkercad](./img/ArduinoTinkercad.jpg)


## Integrantes 
- Belen Soria


## Practica domiciliaria: Sistema Montacargas.
![Tinkercad](./img/Montacargas.png) ![Tinkercad](./img/DiagramaEsquematico.png)


## Descripción
Mi proyecto es un modelo de montacarga funcional para un hospital.
Este posee un sistema que puede recibir ordenes de subir, bajar o pausar desde diferentes pisos y
muestre el estado actual del montacargas en el display 7 segmentos.

## Función principal

Esta funcion se encarga de ejecutar el display cada 3 segundos. Y permite que se pueda leer el estado de los botones.

actual y anterior son variables globales que almacen el tiempo actual 
contadorSistemaDisplay, estadoSistema también son variables globales que se encargan de cambiar el numero en el display.

Esta funcion toma el tiempo actual y le resta el tiempo anterior desde que se ejecutó, si es menor al intervalo de tiempo
entre cada piso lo muestra por el display incrementandolo.
Dicho anteriormente, esta función permite que los botones puedan ser leídos simultaneamente usando la funcion millis.

~~~ C (lenguaje en el que esta escrito)

void EjecutarDisplay(int *actual, int *anterior, int intervalo)
{
  if (*actual - *anterior> intervalo)
  {
    Serial.print("Estado actual montacarga: piso: ");
    contadorSistemaDisplay = contadorSistemaDisplay + estadoSistema;
    
    if(contadorSistemaDisplay > 9)
    { 
      contadorSistemaDisplay = 9;
      estadoSistema = 0;
    }
    else
    {
      if(contadorSistemaDisplay < 0)
      {
        Serial.println("Presione: subir");
        contadorSistemaDisplay = 0;
        estadoSistema = 0;
      }
    }
  	Serial.println(contadorSistemaDisplay);
    
    MostrarNumeroDisplay(contadorSistemaDisplay, estadoSistema);
    
    *anterior = millis();
  }
}
~~~

## Sistema Montacargas: diagrama esquemático.
![Tinkercad](./img/DiagramaEsquematico.png)

## Descripción
Mi proyecto es un modelo de montacarga funcional para un hospital.
Este posee un sistema que puede recibir ordenes de subir, bajar o pausar desde diferentes pisos y
muestre el estado actual del montacargas en el display 7 segmentos.
~~~ C (lenguaje en el que esta escrito)
//Enciende cada led del display dependiendo el estado que recibe
void MostrarNumero(int estadoA, int estadoB,int estadoC, int estadoD, int estadoE, int estadoF, int estadoG)
{
  digitalWrite(LED_A, estadoA);
  digitalWrite(LED_B, estadoB);
  digitalWrite(LED_C, estadoC);
  digitalWrite(LED_D, estadoD);
  digitalWrite(LED_E, estadoE);
  digitalWrite(LED_F, estadoF);
  digitalWrite(LED_G, estadoG);
}
~~~
## :robot: Link al proyecto
- [proyecto](https://www.tinkercad.com/things/bMnZ0p5rvni)
## :tv: Link al video del proceso

---






