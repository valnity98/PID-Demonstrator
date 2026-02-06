# PID-Demonstrator – PCB Design  

Dieses Projekt entstand im Rahmen des Master-Studiengangs **Mechatronik und Robotik** (Frankfurt UAS, SoSe 2025) im Fach *Simulation und Regelung*. Ziel war die Entwicklung eines  **PID-Demonstrators**, mit dem die Wirkungsweise eines PID-Reglers anschaulich und praxisnah vermittelt werden kann.

---

## Projektziel  
Der Demonstrator zeigt das Verhalten eines geschlossenen Regelkreises bestehend aus:  

- **Aktor:** DC-Motor zur Ausgabe einer mechanischen Größe (z. B. Winkelposition)  
- **Sensor:** Rückführung über Potentiometer oder Encoder  
- **Regler-Hardware:** STM32-Mikrocontroller führt die PID-Regelung in Echtzeit aus  
- **Benutzerschnittstelle:** Potentiometer zur Einstellung von Kp, Ki, Kd sowie zur Sollwertvorgabe  
- **Visualisierung:** Ausgabe der Regelgrößen über serielle Schnittstelle und LCD  
- **Energieversorgung:** Akkubetrieb über Powerbank, mobiler Einsatz möglich  

Damit können in Echtzeit Effekte wie **Überschwingen, Einschwingzeit, Genauigkeit und Regelabweichung** beobachtet werden.  

---

##  Mein Beitrag: PCB-Design  
Mein Fokus lag auf der **Entwicklung und Umsetzung der Leiterplatte** sowie ein kleiner zusätzlicher Beitrag zur Bestimmung der PID-Parametrisierung mithilfe des MATLAB PID-Tuners. Diese integriert die zentralen Hardware-Komponenten:  

- **Powerbank-Interface** mit Spannungsregelung (12 V, 6 V, 5 V, 3.3 V)  
- **Motorstrom-Messung** über Shunt und INA138  
- **Treiberstufe** mit DRV8848 H-Brücke für Motorsteuerung  
- **Anschlüsse für Potentiometer** zur PID-Parametereinstellung  
- **Header für LCD-Display** und serielle Schnittstellen  
- **Anschluss des STM32F4-Discovery Boards** als Recheneinheit
- **PID-Parametrierung** mithilfe des MATLAB PID-Tuners

---

### PCB Layout  
Top-Layer:  
![PCB Top](PID-Demo%20v92_T.png)  

Bottom-Layer:  
![PCB Bottom](PID-Demo%20v92_B.png)  

### Schaltplan  
![Schaltplan](Schaltplan-Demo.png)  


## Quellen  
- Beispielaufbau: [YouTube-Link](https://youtu.be/qKy98Cbcltw?si=HwGLJR-9h6Nvn7Rk)  
