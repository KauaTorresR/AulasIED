import datetime # biblioteca que visa funções para conseguir a data atual.                                                  

tarefas = []                                                                
historico = []                                                              
fila_execucao = []                                                         

def obter_data_atual():
    return datetime.datetime.now().strftime("%d-%m-%Y") # Retorna a data atual no formato dia-mês-ano (DD-MM-AAAA).

# Função de salvamento de tarefas em um arquivo .txt, e sempre mantela atualizada.
def salvar_tarefas_em_arquivo():
    with open("tarefas_salvas.txt", "w", encoding="utf-8") as arquivo:
        if tarefas:
            arquivo.write("Lista de Tarefas:\n") # write é uma função que escreve no arquivo o que está entre as aspas.
            for t in tarefas:
                arquivo.write(f"- {t['descricao']} (Data: {t['data']})\n")
        else:
            arquivo.write("Nenhuma tarefa adicionada.\n")

# Menu de DATAS
def menu_datas():                                                           
    print("\nEscolha uma data para a tarefa:")
    
    print("1. Hoje")                                                         
    print("2. Amanhã")                                                      
    print("3. Data personalizada")                                          
    opcao = input("Digite o número da opção desejada: ")                    

    if opcao == '1':                                                         
        return obter_data_atual() 
    
    elif opcao == '2':                                                      
        data_amanha = datetime.datetime.now() + datetime.timedelta(days=1) #datetime.now() + datetime.timedelta(days=1) é a função que pega a data atual e soma um dia amais, ou seja assim construindo a data de amanhã.
        return data_amanha.strftime("%d-%m-%Y") # Formata a data de amanhã no formato dia-mês-ano (DD-MM-AAAA).
    
    elif opcao == '3':                                                      
        data_str = input("Digite a data no formato DD-MM-AAAA: ")
        try: # try é uma função que tenta executar um bloco de código e se ela não conseguir, ele ativa o except informando o erro.                                                          
            data = datetime.datetime.strptime(data_str, "%d-%m-%Y") # Converte string para data no formato correto.
            return data.strftime("%d-%m-%Y")
        except ValueError: # except ValueError é uma função que trata de um erro de um valor que o usuário digitou. 
            print("Data inválida. Tente Novamente, retornando para o menu...")
            return None # ao ativar essa função o usuário retorna de volta para o menu, e o valor digitado não retorna.
    else:
        print("Opção inválida. Tente Novamente, retornando para o menu...")
        return None # ao ser ativado a estrutura else, o usuário digitou um valor para uma opção errada, assim retornando para o menu.

# principais funções.
def adicionar_tarefa(tarefa):
    data = menu_datas()
    if data is None:
        return # Se a data for inválida retorna para o menu sem adicionar a tarefa.
    tarefa_completa = {"descricao": tarefa, "data": data}
    tarefas.append(tarefa_completa) # append usada em estruturas que deseja adicionar um conteúdo a uma lista, nesse caso a lista de tarefas.
    historico.append(tarefa_completa)
    fila_execucao.append(tarefa_completa)
    salvar_tarefas_em_arquivo() # Salvar automaticamente
    print(f"Tarefa '{tarefa_completa['descricao']}' adicionada para {tarefa_completa['data']}!\n")

def remover_tarefas():
    if historico:
        ultima = historico.pop()
        tarefas.remove(ultima) # remove é uma função que remove o último elemento da lista no formato pilha (first in last out).
        fila_execucao.remove(ultima)
        salvar_tarefas_em_arquivo() # Salvar automaticamente
        print(f"Tarefa '{ultima['descricao']}' removida!\n")
    else:
        print("Não existe nenhuma tarefa para remover. Crie uma!\n")

def concluir_tarefas():
    if fila_execucao:
        feita = fila_execucao.pop(0) # pop é uma função que é usada para remover conteúdos de uma lista.
        tarefas.remove(feita)
        salvar_tarefas_em_arquivo() # Salvar automaticamente
        print(f"Tarefa '{feita['descricao']}' concluida!\n")
    else:
        print("Não existe nenhuma tarefa para concluir. Crie uma!\n")

def mostrar_tarefas():
    print("\n Lista de Tarefas:")
    if tarefas:
        for i, t in enumerate(tarefas): # enumerate é uma função que retorna o índice e o valor de cada elemento da lista.
            print(f"{i + 1}. {t['descricao']} (Data: {t['data']})")
    else:
        print("Nenhuma tarefa adicionada.")
    print("\n Tarefas Pendentes: ")
    if fila_execucao:
        hoje = obter_data_atual()
        fila_execucao.sort(key=lambda t: (t['data'] != hoje, t['data'])) # sort é uma função que ordena os elementos de uma lista. lambda é uma função anônima que pode ser usada para criar funções simples.
        for i, t in enumerate(fila_execucao):
            print(f"{i + 1}. {t['descricao']} (Data: {t['data']})")
    else:
        print("Nenhuma tarefa pendente.")

# menu principal.
while True: # while true é uma estrutura de looping que executa o sistema ate que o usuário decida sair, no caso a opção 5.
    print("---------------Menu de Tarefas--------------- \n")
    print("|| ||")
    print("|| 1. Adicionar tarefa. ||")
    print("|| 2. Desfazer tarefas (modo pilha). ||")
    print("|| 3. Concluir tarefas (modo fila). ||")
    print("|| 4. Mostrar tarefas e tarefas pendentes. ||")
    print("|| 5. Sair do sistema. ||")
    print("|| ||\n")
    print("---------------------------------------------")

    opcao = input("Escolha uma opção: ") # opcao é uma variável que armazena o valor digitado pelo usuário e percorre as estruturas if, elif, else e aciona uma condição.

    if opcao == '1':
        tarefa = input("Digite a tarefa: ")
        adicionar_tarefa(tarefa)
    elif opcao == '2':
        remover_tarefas()
    elif opcao == '3':
        concluir_tarefas()
    elif opcao == '4':
        mostrar_tarefas()
    elif opcao == '5':
        print("Saindo do programa...")
        break # break é uma função que interrompe o loop do while de acordo com a vontade do usuário.
    else:
        print("Opção inválida, voltando para o sistema...\n")
