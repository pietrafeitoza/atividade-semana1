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
