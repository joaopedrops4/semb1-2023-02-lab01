# Questionário Sistemas Embarcados I

## 1. Explique brevemente o que é compilação cruzada (***cross-compiling***) e para que ela serve.

 ﻿ A compilação cruzada, ou “cross-compiling”, é um processo que envolve a compilação de um código para que esse possa ser executado em uma plataforma ou sistema operacional diferente daquele no qual o código está sendo compilado. Por exemplo, você pode estar usando um sistema operacional baseado em Windows, mas deseja compilar seu código para que o mesmo seja executado em um sistema Linux. Nesse caso, você usaria um compilador cruzado.
   
## 2. O que é um código de inicialização ou ***startup*** e qual sua finalidade?

  ﻿O código de inicialização, também conhecido como “startup”, é um conjunto de instruções que são executadas quando um programa começa a rodar. Ele é responsável por configurar o ambiente de execução do programa antes que o código principal seja executado e tem como finalidades: Inicialização do hardware; Carregamento do sistema operacional e Transferência de controle.
   
## 3. Sobre o utilitário **make** e o arquivo **Makefile responda**:

#### (a) Explique com suas palavras o que é e para que serve o **Makefile**.

  O “makefile” é um conjunto de tarefas que proporciona a utilização do atalho “make”, que é responsável pela automatização do processo de compilação e linkagem de programas. O “makefile” é um tipo de documentação e de forma mais geral pode ser utilizado para diversos tipos de hardware.
  
#### (b) Descreva brevemente o processo realizado pelo utilitário **make** para compilar um programa.

  O utilitário “make” é uma ferramenta que automatiza o processo de compilação e construção de programas. Esse utilitário, através de um conjunto de instruções chamado “makefile”, possibilita a execução das regras previamente estabelecidas e assim consegue compilar um programa. 

#### (c) Qual é a sintaxe utilizada para criar um novo **target**?

   De forma generalizada a sintaxe de um “target” é descrita por:
   ###### targets: prerequisites
   ######          recipe  
   ###### Variáveis
   CC=arm-none-eabi-gcc
   CFLAGS=-g -mcpu=cortex-m4 -mthumb -O0 -Wall
   ###### Regra
   main.o: main.c
           $(CC) -c $(CFLAGS) main.c -o main.o
   ###### No exemplo acima main.o é o arquivo destino, main.c é o arquivo dependência e $(CC) -c $(CFLAGS) main.c -o main.o é a regra pré-estabelecida.
        
#### (d) Como são definidas as dependências de um **target**, para que elas são utilizadas?

   As dependências de um “target” são definidas após a criação do alvo propriamente dito a partir do operador dois pontos ( : ). As dependências são os arquivos dos quais o alvo depende para ser construído, ou seja, é a partir da dependência que o “make” permite a criação do “target” dado o pré-requisito estabelecido pelo usuário.

#### (e) O que são as regras do **Makefile**, qual a diferença entre regras implícitas e explícitas?

  As regras do “makefile” são as instruções que definem como criar um arquivo destino a partir de certa dependência. As regras explícitas informam ao “make” quais arquivos dependem de outros arquivos, bem como os comandos necessários para compilar um determinado arquivo. Já as regras implícitas informam ao “make” quais são os comandos a serem executados para a compilação do programa como um todo.

## 4. Sobre a arquitetura **ARM Cortex-M** responda:

### (a) Explique o conjunto de instruções ***Thumb*** e suas principais vantagens na arquitetura ARM. Como o conjunto de instruções ***Thumb*** opera em conjunto com o conjunto de instruções ARM?

   O conjunto de instruções Thumb é uma extensão da arquitetura ARM que foi projetada para melhorar a eficiência do código em sistemas com restrições de memória. O conjunto de instruções “thumb” consiste em atuar como um resumo compacto das instruções ARM. Enquanto as instruções ARM possuem 32 bits, uma função “thumb” possui 16 bits.

### (b) Explique as diferenças entre as arquiteturas ***ARM Load/Store*** e ***Register/Memory***.

   A arquitetura ARM Load/Store é uma arquitetura do tipo RISC(Reduced Instruction Set Computing), que utiliza um modelo de acesso à memória baseado em carregamento e armazenamento. Nessa arquitetura, apenas instruçoes de carregamento(load) e armazenamento(store) podem acessar a memória. Já a arquitetura ARM Register/Memory é uma arquitetura do tipo CISC(Complex Instruction Set Computing) que permite um dos operandos operar na memória enquanto o outro opera no registrador, ou seja, permite que as operações ocorram diretamente na memória.

### (c) Os processadores **ARM Cortex-M** oferecem diversos recursos que podem ser explorados por sistemas baseados em **RTOS** (***Real Time Operating Systems***). Por exemplo, a separação da execução do código em níveis de acesso e diferentes modos de operação. Explique detalhadamente como funciona os níveis de acesso de execução de código e os modos de operação nos processadores **ARM Cortex-M**.

   Os processadores ARM Cortex-M possuem dois níveis de acesso e dois modos de operação. Para os níveis de acesso: Nível de Acesso Privilegiado(PAL) é quando o código é executado em um nível que proporciona acesso total aos recursos do processador e aos registradores restritos; Nível de Acesso Sem-Privilégios(NPAL) é quando o código não tem acesso aos registradores restritos do sistema. Para os modos de operação: Modo Thread é o modo onde o processador pode operar em ambos os níveis de acesso, PAL e NPAL; Modo Handler é quando o processador sempre opera no nível de acesso PAL.

### (d) Explique como os processadores ARM tratam as exceções e as interrupções. Quais são os diferentes tipos de exceção e como elas são priorizadas? Descreva a estratégia de **group priority** e **sub-priority** presente nesse processo.

   Os processadores ARM tratam exceções e interrupões de maneira eficiente e versátil. Quando ocorre uma exceção ou interrupção, a execução faz a transição do modo usuário para o modo kernel onde a exceção ou interrupção é tratada, e também, o processador entra no modo Handler quando ocorre uma exceção. As interrupções são caracterizadas entre FIQ(Fast Interrupt Request) e IRQ(Interrupt Request)

### (e) Qual a diferença entre os registradores **CPSR** (***Current Program Status Register***) e **SPSR** (***Saved Program Status Register***)?

   O registrador CPSR mantém bits de estado que indicam o resultado de operações lógicas e aritméticas, controlam interrupções e o modo de operação do processador enquanto o registrador SPSR está presente apenas em modos de exceção e é usado para guardar o valor de CPSR quando uma exceção associada é chamada. Ou seja, o CPSR é usado para controlar o estado atual do programa enquanto o SPSR é usado para salvar o estado do programa durante uma interrupção ou exceção.

### (f) Qual a finalidade do **LR** (***Link Register***)?

   O “Link Register” é um registrador que tem a função de armazenar o enndereço de retorno quando uma chamada de sub-rotina é concluída. A sua finalidade consiste em permitir chamadas mais rápidas para sub-rotinas e em casos de exceção, ele faz com que o endereço de retorno seja empurrado para a pilha através do hardware.

### (g) Qual o propósito do Program Status Register (PSR) nos processadores ARM?

   O PSR é um registrador que permite indicar o resultado de operações lógicas e aritméticas, controlam interrupções e o modo de operação do processador. Ele é dividido em: APSR(Application Program Status Register) que são flags utilizadas como operações de instrução; ISPR(Interrupt Program Status Register) que indicam a exceção de interrupção processada e ESPR(Execution Program Status Register) que controlam a operação de certas instruções.

### (h) O que é a tabela de vetores de interrupção?

   A tabela de vetores de interrupção é uma tabela de endereços de memória que apontam para as rotinas de tratamento de interrupções. Quando uma interrupção é gerada o processador salva o seu estado atual e começa a executar o tratamento de interrupção apontado pelo vetor, o que garante que nenhuma das tarefas executadas pelo sistema operacional entrem em conflito.

### (i) Qual a finalidade do NVIC (**Nested Vectored Interrupt Controller**) nos microcontroladores ARM e como ele pode ser utilizado em aplicações de tempo real?

   O NVIC é um controlador de interrupções presente nos microcontroladores ARM e tem como funcionalidades a manipulação de interrupções, a resposta rápida com baixa latência e a configuração personalizada das interrupções. Em aplicações de tempo real, o NVIC permite que o sistema responda rapidamente a eventos de interrupção, o que é crucial para manter o desempenho em tempo real do microcontrolador. Além disso, a capacidade de priorizar interrupções permite que os desenvolvedores garantam que as tarefas mais críticas sejam atendidas primeiro.

### (j) Em modo de execução normal, o Cortex-M pode fazer uma chamada de função usando a instrução **BL**, que muda o **PC** para o endereço de destino e salva o ponto de execução atual no registador **LR**. Ao final da função, é possível recuperar esse contexto usando uma instrução **BX LR**, por exemplo, que atualiza o **PC** para o ponto anterior. No entanto, quando acontece uma interrupção, o **LR** é preenchido com um valor completamente  diferente,  chamado  de  **EXC_RETURN**.  Explique  o  funcionamento  desse  mecanismo  e especifique como o **Cortex-M** consegue fazer o retorno da interrupção. 

   O mecanismo *EXC_RETURN* é um valor especial carregado pelo “Link Register” usado quando uma interrupção ocorre em um processador ARM Cortex-M. Este valor não é um endereço de retorno, mas sim um valor que contém informações sobre o estado do processador antes da interrupção. Dito isso, o *EXC_RETURN* permite que o processador interrompa uma execução normal do programa para tratar uma interrupção e, e seguida, retorne ao programa exatamente de onde ocorreu a parada.

### (k) Qual  a  diferença  no  salvamento  de  contexto,  durante  a  chegada  de  uma  interrupção,  entre  os processadores Cortex-M3 e Cortex M4F (com ponto flutuante)? Descreva em termos de tempo e também de uso da pilha. Explique também o que é ***lazy stack*** e como ele é configurado. 

  No Cortex-M3 quando uma interrupção ocorre o processador salva automaticamente o estado do programa incluindo 8 registradores e o *EXC_RETURN* do “Link Register” caso haja mudanças na pilha enquanto no Cortex-M4F, o suporte a ponto flutuante permite que o processador salve automaticamente o estado do programa porém incluindo 26 registradores, o que pode levar mais tempo e usar mais espaço na pilha que o Cortex-M3. Já o *Lazy Stack* é um recurso do Cortex-M4F que ajuda a otimizar o uso da pilha e o tempo de interrupções, os registradores só são empilhados se forem usados durante a execução da rotina de tratamento de interrupção. Para configurar o *Lazy Stack* é necessário habilitar o bit FPCA(Floating-Point Context Active) no registrador de controle, onde esse bit é usado para indicar se o contexto do ponto flutuante está ativo, assim, permitindo que o processador empilhe os registradores caso haja ocorrência de interrupção.


## Referências

### Básicas

[1] [STM32F411xC Datasheet](https://www.st.com/resource/en/datasheet/stm32f411ce.pdf)

[2] [RM0383 Reference Manual](https://www.st.com/resource/en/reference_manual/rm0383-stm32f411xce-advanced-armbased-32bit-mcus-stmicroelectronics.pdf)

[3] [Using the GNU Compiler Collection (GCC)](https://gcc.gnu.org/onlinedocs/gcc/index.html)

[4] [GNU Make](https://www.gnu.org/software/make/manual/html_node/index.html)

### Vídeos Microsoft Teams

[5] [05 - Introdução à arquitetura de computadores](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[6] [06 - Arquitetura Cortex-M Parte 1/2](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[7] [07 - Arquitetura Cortex-M Parte 2/2](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[8] [08 - Microcontroladores STM32](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[9] [10 - Introdução à arquitetura de computadores](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

### Material Suplementar

[5] [A General Overview of What Happens Before main()](https://embeddedartistry.com/blog/2019/04/08/a-general-overview-of-what-happens-before-main/)
 
[6] [Bare metal embedded lecture-1: Build process](https://youtu.be/qWqlkCLmZoE?si=mn5yDnJYudQ1PpZH)
 
[7] [Bare metal embedded lecture-2: Makefile and analyzing relocatable obj file](https://youtu.be/Bsq6P1B8JqI?si=yuNLPj3JQ-2IT1yo)
 
[8] [Bare metal embedded lecture-3: Writing MCU startup file from scratch](https://youtu.be/2Hm8eEHsgls?si=c27MpZ47ApiMSwHR)
 
[9] [Lecture 15: Booting Process](https://youtu.be/3brOzLJmeek?si=MsHRUEJP8zofjwJQ)
