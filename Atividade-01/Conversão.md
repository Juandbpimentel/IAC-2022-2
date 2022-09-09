# Programa para conversão de horas, minutos e segundos em seguntos totais

## 1 - Validação da hora (Checar se é maior que 24)

    # Pega as horas -> subtrai por 25 -> checa se é maior que -1  --|
    # 																|
    # ---------------------------------------------------------------
    # |
    # ---> se for maior entra na instrução de tratamento de erro (0F0)
    # |
    # |--> se não for continua a execução normalmente

    000 01 100 06 105
    001 0F 0F0 0D 002

## 2 - Conversão de hora em segundos e incremento no reg. de soma
    
    # Horas válidas, Coloca as horas no mq ---> multiplica por 3600--|
    # ----------------------------------------------------------------
    # |
    # ---> coloca o resultado do mq no ac---> soma o resultado-|
    #  	      												   |
    #  ---------------------------------------------------------
    #  |
    #  |
    #  ---> guarda o resultado ----> continua a execução

    002 09 100 0B 108
    003 0B 108 0A 000
    004 05 10E 21 10E

## 3 - Validação dos minutos (Checar se é maior que 60)

    # Pega os minutos -> subtrai por 61 -> checa se é maior que -1 -|
    # 																|
    # ---------------------------------------------------------------
    # |
    # ---> se for maior entra na instrução de tratamento de erro (0F0)
    # |
    # |--> se não for continua a execução normalmente

    005 01 101 06 106
    006 0F 0F0 0D 007

## 4 - Conversão de minutos em segundos e incremento no reg. de soma

    # Minutos válidos, coloca os minutos no mq ---> multiplica por 60 ---|
    # --------------------------------------------------------------------
    # |
    # ---> coloca o resultado do mq no ac---> soma o resultado--|
    #  	      													|
    #  ----------------------------------------------------------
    #  |
    #  |
    #  ---> guarda o resultado ----> continua a execução

    007 09 101 0B 108
    008 0A 000 05 10E 
    009 21 10E 0D 00A

## 5 - Validação de segundos (Checar se é maior que 60)

    # Pega os segundos -> subtrai por 61 -> checa se é maior que -1--|
    # 																 |
    # ----------------------------------------------------------------
    # |
    # ---> se for maior entra na instrução de tratamento de erro (0F0)
    # |
    # |--> se não for continua a execução normalmente

    00A 01 102 06 106
    00B 0F 0F0 0D 00C

## 6 - Incremento de segundos no reg. de soma

    # Segundos válidos, soma os segundos ao resultado-----------|
    #  	      													|
    #  ----------------------------------------------------------
    #  |
    #  |
    #  ---> guarda o resultado ----> continua a execução

    00C 01 102 05 10E
    00D 21 10E 0D 00F

## 7 - Tratamento de Erro caso algum dos números seja maior que o valor máximo

    # Tratamento de erro(Carrega a constante -1 no ac e Guarda -1 no resultado) --> encerramento
    0F0 01 10B 21 10E
    0F1 00 000

## 8 - Registradores utilizados

    100 18  			# horas
    101 3C  			# minutos
    102 3C  			# segundos
    105 19			# constante  25
    106 3D			# constante  61
    107 18			# constante  24
    108 3C			# constante  60
    109 1			# constante  1
    10B FFFFFFFFFF  # constante -1
    10E 0			# resultado

## Tabela de referência de Comandos do IAS

    # transferência de dados:
    #		_____________________________________	
    #		| func	   |	Bin		|    Hex    |
    #		|Load mq   |  00001010	|     0A    |
    #		|Load mq,x |  00001001	|     09    |
    #		|load m    |  00000001	|     01    |
    #		|stor      |  00100001	|     21    |
    #		|	   	   |			|	 	    |
    # jump incondicional: 
    #		
    #		|jump M esq|  00001101	|     0D    |
    #		|jump M dir|  00001110	|     0E    |
    #		|	  	   |			|		    |
    # jump condicional: 
    #		
    #		|jump M esq|  00001101	|     0F    |
    #		|jump M dir|  00001110	|     10    |
    #		|	  	   |			|		    |
    # Aritimética:
    #		|add  M    |  00000101	|     05    |
    #		|sub  M    |  00000110	|     06    |
    #		|mul  M    |  00001011	|     0B    |
    #		|div  M    |  00001100	|     0C    |
    #		|RSH       |  00010101	|     15    |
    #		-------------------------------------

#   Codigo Completo

    # Pega as horas -> subtrai por 25 -> checa se é maior que -1  --|
    # 																|
    # ---------------------------------------------------------------
    # |
    # ---> se for maior entra na instrução de tratamento de erro (0F0)
    # |
    # |--> se não for continua a execução normalmente

    000 01 100 06 105
    001 0F 0F0 0D 002



    # Horas válidas, Coloca as horas no mq ---> multiplica por 3600--|
    # ----------------------------------------------------------------
    # |
    # ---> coloca o resultado do mq no ac---> soma o resultado-|
    #  	      												   |
    #  ---------------------------------------------------------
    #  |
    #  |
    #  ---> guarda o resultado ----> continua a execução

    002 09 100 0B 108
    003 0B 108 0A 000
    004 05 10E 21 10E



    # Pega a minutos -> subtrai por 61 -> checa se é maior que -1 --|
    # 																|
    # ---------------------------------------------------------------
    # |
    # ---> se for maior entra na instrução de tratamento de erro (0F0)
    # |
    # |--> se não for continua a execução normalmente

    005 01 101 06 106
    006 0F 0F0 0D 007




    # Minutos válidos, multiplica por 60 e soma o resultado---|
    # ---------------------------------------------------------
    # |
    # ---> coloca o resultado do mq no ac---> soma o resultado--|
    #  	      													|
    #  ----------------------------------------------------------
    #  |
    #  |
    #  ---> guarda o resultado ----> continua a execução

    007 09 101 0B 108
    008 0A 000 05 10E 
    009 21 10E 0D 00A




    # Pega os segundos -> subtrai por 61 -> checa se é maior que -1--|
    # 																 |
    # ----------------------------------------------------------------
    # |
    # ---> se for maior entra na instrução de tratamento de erro (0F0)
    # |
    # |--> se não for continua a execução normalmente

    00A 01 102 06 106
    00B 0F 0F0 0D 00C



    # Segundos válidos, multiplica por 3600 e soma o resultado---|
    # ---------------------------------------------------------
    # |
    # ---> coloca o resultado do mq no ac---> soma o resultado--|
    #  	      													|
    #  ----------------------------------------------------------
    #  |
    #  |
    #  ---> guarda o resultado ----> continua a execução

    00C 01 102 05 10E
    00D 21 10E 0D 00F


    # Tratamento de erro(Carrega a constante -1 no ac e Guarda -1 no resultado) --> encerramento
    0F0 01 10B 21 10E
    0F1 00 000




    100 18  			# horas
    101 3C  			# minutos
    102 3C  			# segundos
    105 19			# constante  25
    106 3D			# constante  61
    107 18			# constante  24
    108 3C			# constante  60
    109 1			# constante  1
    10B FFFFFFFFFF  # constante -1
    10E 0			# resultado