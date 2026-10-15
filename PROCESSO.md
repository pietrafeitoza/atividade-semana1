# Laboratório - aula 1

## 1. Contextualizar

O objetivo dessa atividade é analisar, por meio de um projeto de arduino simples, sua possível aplicação no nosso projeto. Nesse caso, temos um liga e desliga do LED, que, na interpretação do nosso projeto poderia indicar o estado do dispositivo. No código, há um loop que descreve que o LED fica acesso a cada 0,2 segundos e permanece desligado por 1,8 segundos. O critério de aceitação é exatamente esse, juntamente com a definição do PINO_LED na porta 8 e a corrente calculada abaixo de 20mA.
Pretendo delegar à IA o que não consigo deduzir logicamente, fazendo uma pergunta descrita no tópico seguinte e entender melhor coisa

## 2. Consultar
   "Eu poderia colocar dois resistores ligado a um led? E por quê alguém faria isso?"

Resposta Gemini:


Sim, você pode colocar dois resistores ligados a um mesmo LED.

### Por que usar dois resistores em um LED?

1. **Falta de componente no estoque:**
Se você não tem o valor exato (ex: 220 $\Omega$), combina dois que já possui:
* **Em série (soma):** $100\ \Omega + 120\ \Omega = 220\ \Omega$
* **Em paralelo (divide):** Dois de $470\ \Omega$ em paralelo $\approx 235\ \Omega$


2. **Dividir a potência (não queimar o resistor):**
Resistores comuns aguentam até $0{,}25\text{ W}$. Se o circuito gerar mais calor do que isso, usar dois resistores divide a energia e evita que eles queimem.
3. **Valores específicos de precisão:**
Nem todos os valores de resistência são vendidos no mercado. Combinar resistores permite criar valores customizados.
4. **Proteção + Ajuste (Potenciômetro):**
Um resistor fixo garante que o LED nunca receba corrente excessiva, enquanto um potenciômetro em série permite ajustar o brilho manualmente.

---

### Como conectar?

* **Série (atrás do outro):** Aumenta a resistência total $\rightarrow$ Diminui o brilho.
`Pino Arduino ---> [R1] ---> [R2] ---> [LED] ---> GND`
* **Paralelo (lado a lado):** Diminui a resistência total $\rightarrow$ Aumenta o brilho.
`Pino Arduino ---> [R1 // R2] ---> [LED] ---> GND`

## 3. Confrontar

A afirmação técnica que quero confrontar/conferir:

"a animação circuito-led do material de apoio: mova o resistor para 100 Ω e para 1 kΩ e compare a corrente com o seu cálculo. O Wokwi não muda o brilho do LED com o valor do resistor nem mede corrente no Uno, então essa conferência é por cálculo e pela animação."

Ao contrário do que a frase afirma, o simulador Wokwi altera sim a intensidade e a renderização do LED de acordo com a resistência, simulando como acontece realmente na vida real. De fato, a placa Arduino Uno no Wokwi não possui um instrumento de medição embutido no próprio chip para mostrar a corrente no pino, sendo necessário usar o cálculo teórico ou adicionar um componente de amperímetro para conferir a corrente que flui no circuito.

## 4. Construir

https://wokwi.com/projects/477967199508674561

![alt text](<Captura de tela 2026-10-15 141422.png>)

## 6. Comprovar

Qual corrente passa pelo LED com 330 Ω? Escreva o cálculo e depois confira na animação circuito-led.

Se U = R . I

Temos que a tensão sobre o resistor é de 5 - 2, sendo 3 V.

Substituindo 3 = 330 . I 
I = 0,00909 aprox 9,1 mA

Por que um resistor de 0 Ω queima o LED na placa real?

Um resistor de 0 Ω faria com que a corrente inteira passasse para o LED, dando uma descarga maior do que pode receber.

O que muda no código se o LED for para o pino 12?

O código apenas trocaria a parte:
<const int PINO_LED = 8;> por
<const int PINO_LED = 12;>