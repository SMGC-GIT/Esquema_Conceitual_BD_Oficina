# **DESAFIO DE PROJETO DIO x HEINEKEN** 🍺

## **Criando um Projeto Conceitual de Banco de Dados - Oficina Mecânica**

---

## **Descrição do Projeto**

📚 Este projeto faz parte do bootcamp **DIO x HEINEKEN - Inteligência Artificial Aplicada a Dados com Copilot** e envolve a criação de um esquema conceitual de banco de dados para o gerenciamento de uma oficina mecânica.  
🎯 O objetivo é modelar um sistema de controle e execução de ordens de serviço (OS), representando os relacionamentos entre clientes, veículos, mecânicos, serviços e peças.

A partir da narrativa fornecida, todas as entidades, relacionamentos e atributos foram criados. Caso algo não esteja claramente definido, explicações e suposições são descritas abaixo para auxiliar na avaliação.

---

## **Narrativa**

- Clientes levam veículos à oficina para serviços de conserto ou revisão periódica.
- Cada veículo é designado a uma equipe de mecânicos que identifica os serviços a serem executados e preenche uma **Ordem de Serviço (OS)**.
- Cada OS contém: número, data de emissão, valor total, status e data prevista de conclusão.
- O valor da OS é calculado a partir dos serviços realizados (consultando uma tabela de referência de mão de obra) e das peças utilizadas.
- Os mecânicos possuem código, nome, endereço e especialidade.
- O cliente autoriza a execução dos serviços antes da equipe começar os trabalhos.
- A mesma equipe avalia e executa os serviços solicitados.

---

## **Estrutura Proposta do Esquema**

| **Entidade**     | **Atributos**                                                                                     |
|------------------|--------------------------------------------------------------------------------------------------|
| **Cliente**      | ID, Nome, Telefone, Endereço                                                                     |
| **Veículo**      | ID_Veículo, Marca, Modelo, Ano, Placa, ID_Cliente                                                |
| **Mecânico**     | ID_Mecânico, Nome, Endereço, Especialidade                                                       |
| **Ordem de Serviço (OS)** | Número_OS, Data_Emissão, Data_Conclusão, Valor_Total, Status, ID_Veículo, ID_Equipe      |
| **Serviço**      | ID_Serviço, Descrição, Valor_Mão_de_Obra                                                         |
| **Peça**         | ID_Peça, Nome, Valor                                                                            |
| **Equipe**       | ID_Equipe, Nome_Equipe                                                                          |
| **Equipe_Mecânico** | ID_Equipe, ID_Mecânico                                                                        |
| **Serviço_OS**   | Número_OS, ID_Serviço, Quantidade                                                               |
| **Peça_OS**      | Número_OS, ID_Peça, Quantidade                                                                  |

---

### **Relacionamentos**

- **Cliente ↔ Veículo**: Um cliente pode ter vários veículos, mas cada veículo pertence a um único cliente (1:N).
- **Veículo ↔ OS**: Um veículo pode gerar várias ordens de serviço, mas cada OS pertence a um único veículo (1:N).
- **Equipe ↔ Mecânico**: Uma equipe pode ter vários mecânicos, e um mecânico pode participar de várias equipes (N:N).
- **OS ↔ Equipe**: Uma OS é atribuída a uma única equipe, e uma equipe pode atender a várias OS (1:N).
- **OS ↔ Serviço**: Uma OS pode incluir vários serviços, e cada serviço pode ser usado em várias OS (N:N).
- **OS ↔ Peça**: Uma OS pode incluir várias peças, e cada peça pode ser usada em várias OS (N:N).

---


## **Suposições Adicionais**

- A narrativa não menciona explicitamente dados de contato do cliente, mas foi assumido que `Telefone` e `Endereço` seriam úteis para o contexto de uma oficina.
- Cada veículo deve ter uma identificação única (como a Placa) para evitar ambiguidades.
- O status da OS pode incluir valores como "Pendente", "Em Execução" e "Concluído".
- Cada mecânico deve possuir uma especialidade para facilitar a organização das equipes.

---

## **Agradecimentos**

Agradeço à equipe da **DIO** e **HEINEKEN** pela oportunidade de participar deste desafio e ampliar minhas habilidades em modelagem de banco de dados e organização estrutural de informações.  
Este projeto reflete o aprendizado prático e meu compromisso com boas práticas na área de tecnologia.

---
