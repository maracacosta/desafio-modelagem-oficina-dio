# 🔧 Projeto de Banco de Dados - Oficina Mecânica

Este projeto foi desenvolvido como parte do **Bootcamp DIO - Coding the Future Heineken: IA para Análise de Dados**, com o objetivo de criar um esquema conceitual e lógico de banco de dados para controle de ordens de serviço de uma oficina mecânica.

---

## 📌 Objetivo

Modelar um banco de dados relacional capaz de registrar:

- Informações dos clientes e seus veículos  
- Equipe de mecânicos envolvidos nas ordens de serviço  
- Peças utilizadas  
- Serviços executados  
- Mão de obra aplicada conforme referência  
- Registro detalhado das ordens de serviço com múltiplos serviços, peças e profissionais  

---

## 🧠 Estrutura do Projeto

O projeto foi modelado no **MySQL Workbench** com base no modelo Entidade-Relacionamento (ER).

---

## 🗂️ Entidades Principais

### `Cliente`
| Campo            | Tipo          | Descrição                    |
|------------------|---------------|------------------------------|
| idCliente        | INT (PK)      | Identificador do cliente     |
| Nome Completo    | VARCHAR(100)  | Nome completo do cliente     |
| Telefone         | VARCHAR(15)   | Contato                      |
| Email            | VARCHAR(100)  | E-mail                       |

### `Veículo`
| Campo            | Tipo          | Descrição                    |
|------------------|---------------|------------------------------|
| idVeiculo        | INT (PK)      | Identificador do veículo     |
| Placa            | VARCHAR(10)   | Placa do veículo             |
| Modelo           | VARCHAR(50)   | Modelo do veículo            |
| Ano              | YEAR          | Ano de fabricação            |
| idCliente        | INT (FK)      | Cliente dono do veículo      |

### `Mecânico`
| Campo            | Tipo          | Descrição                    |
|------------------|---------------|------------------------------|
| idMecanico       | INT (PK)      | Identificador do mecânico    |
| Nome Completo    | VARCHAR(100)  | Nome completo                |
| Endereço         | VARCHAR(150)  | Endereço                     |
| Especialidade    | VARCHAR(100)  | Área de atuação              |

### `OrdemServico`
| Campo            | Tipo          | Descrição                    |
|------------------|---------------|------------------------------|
| idOrdemServico   | INT (PK)      | Identificador da OS          |
| idCliente        | INT (FK)      | Cliente que solicitou        |
| idVeiculo        | INT (FK)      | Veículo atendido             |

---

## 🔄 Relacionamentos

### `MecanicoRecebeOS` (M:N)
Relaciona mecânicos a ordens de serviço (caso a OS seja feita por uma equipe).

| Campo            | Tipo          |
|------------------|---------------|
| idMecanico       | INT (FK)      |
| idOrdemServico   | INT (FK)      |

### `Peça`
| Campo            | Tipo          |
|------------------|---------------|
| idPeca           | INT (PK)      |
| Descrição        | VARCHAR(100)  |
| ValorUnit        | DECIMAL(10,2) |

### `ItemPeçaOS`
Relaciona peças às ordens de serviço com quantidade e valor.

| Campo            | Tipo          |
|------------------|---------------|
| idOrdemServico   | INT (FK)      |
| idPeca           | INT (FK)      |
| Quantidade       | INT           |
| ValorUnit        | DECIMAL(10,2) |

### `Serviço`
| Campo            | Tipo          |
|------------------|---------------|
| idServico        | INT (PK)      |
| Descrição        | VARCHAR(100)  |

### `ItemServicoOS`
Registra quais serviços foram executados em uma OS, com o valor da mão de obra efetivamente aplicado.

| Campo            | Tipo          |
|------------------|---------------|
| idOrdemServico   | INT (FK)      |
| idServico        | INT (FK)      |
| ValorMãoObra     | DECIMAL(10,2) |

### `ReferênciaMãoObra`
Tabela de lookup de valores padrão de mão de obra para cada tipo de serviço.

| Campo            | Tipo          |
|------------------|---------------|
| idServico        | INT (FK)      |
| ValorMãoObra     | DECIMAL(10,2) |

---

## 📐 Diagrama Entidade-Relacionamento

O modelo ER foi desenvolvido no MySQL Workbench.

---

## ✅ Conclusão

Este projeto demonstrou a modelagem de um banco relacional com foco em:

- Normalização  
- Integridade referencial  
- Flexibilidade para múltiplos mecânicos, serviços e peças por OS  
- Separação de responsabilidades e lookup tables  

---

## 💻 Ferramentas utilizadas

- MySQL Workbench  
- GitHub  
- DIO Bootcamp Heineken  
- Git  

---

## 🚀 Autora

**Mara Costa**  
