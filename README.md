# Sensor-de-Temperatura
Programa que muestra la temperatura actual y la temperatura promedio




const int sensorPin = A0;




int values=analogRead(sensorPin);




int datos[7]={"\0"};




int cont1=0;



int cont2=0;




int prom=0;




void setup() {





  Serial.begin(9600);
  
  
  
  
}




void loop() {




 
  cont2=cont2+1;
  
  
  
  
  llenado(datos);
  
  
  
  
  ordena(datos);
  
  
  
  
  //imprime(datos);
  
  
  
  
  Serial.println("Temperatura actual: ");
  
  
  
  
  Serial.print(datos[3]);
  
  
  
  
  Serial.println("\n");
  
  
  
  cont1=cont1+datos[3];
  
  
  
  
  prom=cont1/cont2;
  
  
  
  Serial.println("Temperatura promedio: ");
  
  
  
  
  Serial.print(prom);
  
  
  
  
  Serial.println("\n");
  
  
  
  delay(1000);
}

void llenado(int datos[7]) //Aqui se llena el vector con 7 datos
{
  datos[0]={"\0"};
  
  
  
  
  datos[1]={"\0"};
  
  
  
  
  datos[2]={"\0"};
  
  
  
  
  datos[3]={"\0"};
  
  
  
  
  datos[4]={"\0"};
  
  
  
  
  
  datos[5]={"\0"};
  
  
  
  
  datos[6]={"\0"};
  
  
  
  
  int n;
  
  
  
  
  for(n=0;n<7;n++)
  {
    int value = analogRead(sensorPin);
    
    
    
    
    //Serial.println(value);
    
    
    
    
    int volts = round(map(value,0,1023,0,50)); //Se hace la conversion
    
    
    
    
    datos[n]=volts;
    
    
    
    
   //Serial.println("Voltaje: ");
   
   
   
   
    //Serial.print(datos[n]);
    
    
    
    
   // Serial.println("  ");
  }
}




void ordena(int datos[7]) //Se hace el ordenamiento de datos por el metodo burbuja
{
  int k,j,aux;
  
  
  
  
      for(k=0;k<7;k++)
      
      
      
      
      {
        for(j=0;j<6;j++)
        
        
        
        
        {
          if(datos[j]>datos[j+1])
          {
            aux=datos[j];
            
            
            
            
            datos[j]=datos[j+1];
            
            
            
            
            datos[j+1]=aux;
          }
        }
      }
}
void imprime(int datos[7]) //Impresion de los 7 datos
{
  int n;
  
  
  
  
 for(n=0;n<7;n++)
  {
    //Serial.print(datos[n]);
    
    
    
    
    Serial.println("  ");
  }
  Serial.println("\n");
}
