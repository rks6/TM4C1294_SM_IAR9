# TM4C1294_SM_IAR9
Exemplos Assembly ARM Cortex-M (IDE IAR EWARM V9.10)

Ex3

1.

main    MOV R0, #0x55         ; move a constante em 55 em hexadecimal para R0
        MOV R1, R0, LSL #16   ; move R0, com os bits deslocados à esquerda 16 casas, para R1 (ou multiplica R0 por 2^16 e guarda o resultado em R1)
        MOV R2, R1, LSR #8    ; move R1, com os bits deslocados à direita 8 casas, para R2 (ou divide R1 por 2^8 e guarda o resultado em R2)
        MOV R3, R2, ASR #4    ; move R2, com os bits deslocados à direita 4 casas, para R3 (ou divide R2 por 2^4 e guarda o resultado em R3) e mantém o sinal
        MOV R4, R3, ROR #2    ; move os bits de R3 para a direita 2 casas, e os bits retirados no LSB são colocados no MSB, e o resultado guardado em R4
        MOV R5, R4, RRX       ; Faz o que o ROR faz, movendo um bit para a direita, e envolve o bit de carry na operação
          
        B       main          ; retorna ao início da main




• Como valores negativos são codificados?
Em complemento de 2

• É possível visualizar os estados individuais dos flags?
Sim

• Como o PC está relacionado à janela Disassembly?
O PC aponta para a próxima instrução a ser seguida, então o valor que o PC guarda, aparece na Disassembly uma linha destacada, referente à próxima instrução a ser executada.

• Quais instruções são de 16 bits e quais são de 32 bits?
As instruções com extensão .W são de 32 bits (wide) e .N 16 bits (narrow). Então no programa somente a instrução B tem 16 bits.

• Os mnemônicos do disassembly correspondem exatamente aos mnemônicos usados no programa?
Não, como por exemplo, quando há uma pseudo instrução como em " MOV R1, R0, LSL #16 ", aparecerá " LSL.W R1, R0, #16 "

2.

• A construção da aplicação foi bem sucedida?
Sim

• Procure decifrar os resultados de cada operação.
Para simplificar, cada operação continua a mesma da explicada no item 1, mas com um adendo que cada bit passa agora pela operação not antes de ser guardado no registrador.


main    MVN R0, #0x55
        MVN R1, R0, LSL #16
        MVN R2, R1, LSR #8
        MVN R3, R2, ASR #4
        MVN R4, R3, ROR #2
        MVN R5, R4, RRX  
        
        B       main
        
        
