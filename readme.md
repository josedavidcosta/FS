# Recruits Task - Week #2
- ## [git para noobs](https://hackmd.io/@PedroRomao/HJ0GJSae1x)
- ## Add this file to your local git repository create a new branch and work on it, when you are done or as you complete the questions merge the branch into the main branch (remote main branch will have your final work, this means main branch on GitHub, please make the repository public for the next weeks).
- ## Perform the following tasks to the best of your hability, sometimes, in the questions, there are multiple answers just tell us what you think, feel free to use the group to ask questions.

### 1
**1.** Check out the [el-sw repository](https://github.com/fs-feup/el-sw/tree/main) code and documentation  and try to generally understand what the software does in each device (there is no need to understand all the little details).
### 2
When we read values from the brake sensor (C1) and the apps (C3) we do not use the most recent reading and use instead a different approach. Explain the approach and why you think it is used.

**Answer:** Ao fazer a média das ultimas mediçõe os dados sao mais estaveis e evita que o sistema tome decisões imprecisas devido a um dado fora do normal


### 3
Check out the R2D(Ready To Drive) code on the C3 state machine. In the condition below we use a timer (R2DTimer) to check the brake was engaged instead of just checking the brake pressure received from can, why?
```c++
        if ((r2dButton.fell() and TSOn and R2DTimer < R2D_TIMEOUT) or R2DOverride)
        {
            playR2DSound();
            initBamocarD3();
            request_dataLOG_messages();
            R2DStatus = DRIVING;
            break;
        }
```

**Answer:** Ao verificar se o pedal foi acionado por um periodo de tempo evita que o carro entre em r2d acidentalmente
### 4
What is the ID of the can message sent to the bamocar to request torque?
**Answer:** *0x201*
### 5 
The code below is not amazing, tell us some things you would change to improve it, you can write them down in text or correct the code:
```c++

class mycar {
private:
    int sensor_reading[7];
    int vector_size=8; 
    /*
    posição no vetor de cada sensor:
    0; // hydraulic pressure sensor
    1; // temperature sensor
    2; // humidity sensor
    3; // light sensor
    4; // sound sensor
    5; // distance sensor
    6; // accelerometer sensor
    7; // gyroscope sensor
    */
    //retirar sensor_reading9 pq ja n está em uso
public:
    mycar() {
        for (int k = 0; k < vector_size; k++) {
            sensor_reading[k] = 0;
        }
    }

    // Method will update readings by analog reading and print them 
    void updateprint() {
        //trocar os int pelo vector
        for (int u = 0; i < 8; i++) {
            sensor_reading[u] = analogRead(u);
        }
        int i=0;

        while(i<vector_size){
            func(sensor_reading[], i);// print the readings
        }
    }

    //trocar a função para ser chamada varias vezes em vez de só uma fazendo com que se for adicionado um vetor seja mais facil de implementar
    void func(int vector sensor[], pos) {
        Serial.print("Sensor Reading %d: ",pos+1); 
        Serial.println(sensor[pos+1]);

    }
};
