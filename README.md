# Projeto Conceitual - Banco de Dados Oficina

## Descrição
Este projeto tem como objetivo a modelagem conceitual e lógica de um banco de dados para gerenciar uma **Oficina Mecânica**.  
O esquema foi construído para atender aos principais processos do negócio, como:

- Registro de **clientes** e seus respectivos **carros**.  
- Criação e acompanhamento de **ordens de serviço**.  
- Controle de **serviços executados** e **peças utilizadas**.  
- Organização de **equipes de mecânicos** responsáveis pelas ordens de serviço.  

O modelo está estruturado para permitir uma visão completa do fluxo de trabalho da oficina, desde a entrada do veículo até a conclusão do serviço.

---

## Estrutura das Entidades

### **Cliente**
- `idCliente` (PK)  
- `nome`  
- `endereco`  

### **Carro**
- `idCarro` (PK)  
- `marca`  
- `cor`  
- `modelo`  
- `Cliente_idCliente` (FK)  

### **Ordem_servico**
- `idOrdem_servico` (PK)  
- `data_emissao`  
- `data_conclusao`  
- `valor_total`  
- `status`  
- `Equipe_idEquipe` (FK)  
- `Carro_idCarro` (FK)  
- `Carro_Cliente_idCliente` (FK redundante)  

### **Servico**
- `idServico` (PK)  
- `descricao`  
- `valor_referencia`  

### **Ordem_servico_has_Servico** (tabela associativa)
- `Ordem_servico_idOrdem_servico` (FK)  
- `Servico_idServico` (FK)  
- `valor`  

### **Pecas**
- `idPecas` (PK)  
- `descricao`  
- `valor_unitario`  

### **Ordem_servico_has_Pecas** (tabela associativa)
- `Ordem_servico_idOrdem_servico` (FK)  
- `Pecas_idPecas` (FK)  
- `quantidade`  

### **Equipe**
- `idEquipe` (PK)  
- `nome_equipe`  

### **Mecanicos**
- `idMecanicos` (PK)  
- `nome`  
- `endereco`  
- `especialidade`  

### **Mecanicos_has_Equipe** (tabela associativa)
- `Mecanicos_idMecanicos` (FK)  
- `Equipe_idEquipe` (FK)  

---

## Relacionamentos Principais
- **Cliente → Carro**: Um cliente pode ter vários carros.  
- **Carro → Ordem_servico**: Cada ordem de serviço está vinculada a um carro específico.  
- **Ordem_servico → Servico**: Uma ordem de serviço pode conter vários serviços.  
- **Ordem_servico → Pecas**: Uma ordem de serviço pode incluir várias peças.  
- **Equipe → Ordem_servico**: Uma equipe é responsável pela execução de uma ordem de serviço.  
- **Equipe → Mecanicos**: Uma equipe pode ser composta por vários mecânicos.  
