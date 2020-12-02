# Programação arduino
//PULL UP INTERNO//
int led = 3;
int botao = 2;
bool anterior= 1; //boolena (1 ou 0)
bool atual =1; 
int contagem = 0;

  
void setup()
{
  Serial.begin(9600); //Serial.println
  pinMode (botao, INPUT_PULLUP);
  pinMode (led, OUTPUT);
}

void loop()
{
  atual = digitalRead(botao);//verifica se o botão está acionado
    if(!atual && anterior) contagem++;//
   anterior = atual;//salva a contagem
  Serial.println (contagem);//mostra no motor serial
  if (contagem >= 10 && contagem <=15) digitalWrite(led,HIGH);//se as duas confições forem verdadeiras, estiver entre 10 15 acende led
  else digitalWrite (led,LOW);// led apaga se a condição acima for falsa
  if (contagem >15) contagem =0;//reinicia contagem
}

 
