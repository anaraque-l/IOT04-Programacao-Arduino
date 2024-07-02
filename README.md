# IOT04-Programacao-Arduino
 Projeto criado para gerar a melodia da música "Monster" de  da Série Adventure Time na placa arduino. 

código usado para criação do projeto: 

------------------------------------------------------------------
  Aulas Online - LSI-TEC: IOT104 Programação física com Arduino
  Programa/hardware: 012 - Aula 6 - Exercício não Pontuado
  
  Descrição: Criar uma música a sua escolha
-------------------------------------------------------------------*/

#include "frequencias.h"

// Melodia da música Monster - Adventure Time 
int melodia[] = {
C4, E4, G4, A4, G4, E4, C4,
C4, D4, E4, F4, E4, D4, C4,
G4, A4, B4, C5, B4, A4, G4,
E4, F4, G4, A4, G4, F4, E4,
};

// Duração das notas 1/8
int duracaoDasNotas[] = {
  8, 8, 8, 8, 8, 8, 8,
  8, 8, 8, 8, 8, 8, 8,
  8, 8, 8, 8, 8, 8, 8,
  8, 8, 8, 8, 8, 8, 8
};
void setup() {
  //Para Calcular o tamanho da melodia automaticamente
    int tamanhoDaMelodia = sizeof(melodia)/sizeof(int);
  
    for (int essaNota = 0; essaNota < tamanhoDaMelodia; essaNota++) {
    int duracaoDaNota = 1000 /duracaoDasNotas[essaNota];
    tone(8, melodia[essaNota], duracaoDaNota);
    int pausaEntreNotas = duracaoDaNota * 1.30;  
    delay(pausaEntreNotas);
    noTone(8);  
  }
}

void loop()
  // Sem repetição.