dadosF = []
dadosP = []

while True: 
    print("--------Questionário--------")
    print("|| 1. Dados em fila       ||")
    print("|| 2. Dados em pilha      ||")
    print("|| 3. Sair do sistema     ||")
    print("----------------------------")

    opcao = input("Escolha uma opção: ")
    print("\n")

    if opcao == "1":
        nomeF = input("Informe seu nome completo: ")
        dadosF.append(nomeF)
        
        cidadeF = input("Informe sua cidade: ")
        dadosF.append(cidadeF)
        
        while True:
            acesso_transporteF = input("sim/nao. Você tem transporte? ")
            
            if acesso_transporteF == "sim":
                dadosF.append("Sim")
                tipo_transporteF = input("Qual é seu transporte? ")
                dadosF.append(tipo_transporteF)
                
                dadosF = {
                    "Nome": nomeF,
                    "Cidade": cidadeF,
                    "Tem acesso a transporte": acesso_transporteF,
                    "Tipo de transporte": tipo_transporteF
                }
                print(dadosF)
                break
                
            elif acesso_transporteF == "nao":
                dadosF.append("Não")
                justificativaF = input("Por que não tem transporte? ")
                dadosF.append(justificativaF)
                
                dadosF = {
                    "Nome": nomeF,
                    "Cidade": cidadeF,
                    "Tem acesso a transporte": acesso_transporteF,
                    "Justificativa": justificativaF,
                }
                print(dadosF)
                break
                
            else:
                print("Opção inválida. Tente novamente.")
                break
    
    elif opcao == "2":
        nomeP = input("Informe seu nome: ")
        dadosP.append(nomeP)
        
        cidadeP = input("Informe sua cidade: ")
        dadosP.append(cidadeP)
        
        while True:
            acesso_transporteP = input("sim/nao. Você tem transporte? ")
            
            if acesso_transporteP == "sim":
                dadosP.append("Sim")
                tipo_transporteP = input("Qual é seu transporte? ")
                dadosP.append(tipo_transporteP)
                
                dadosP = {
                    "Nome": nomeP,
                    "Cidade": cidadeP,
                    "Tem acesso a transporte": acesso_transporteP,
                    "Tipo de transporte": tipo_transporteP,
                }
                print(dadosP)
                break
                
            elif acesso_transporteP == "nao":
                dadosP.append("Não")
                justificativaP = input("Por que não tem transporte? ")
                dadosP.append(justificativaP)
                
                dadosP = {
                    "Nome": nomeP,
                    "Cidade": cidadeP,
                    "Tem acesso a transporte": acesso_transporteP,
                    "Justificativa": justificativaP,
                }
                print(dadosF)
                break
                
            else:
                print("Opção inválida. Tente novamente.")
                break
            
    elif opcao == "3":
        print("Saindo do sistema...")
        break
    
    else:
        print("Opção inválida. Voltando pra o sistema...")
