
# 📊 Relatório Final — Desafio TelecomX
## Resolução do Challenge Telecom X, desenvolvido pelo Murilo Souza, estudante de Ciência de Dados pela Oracle, na Alura.

## 🧠 Objetivo
Realizei uma análise exploratória de **churn** (evasão de clientes) com base no dataset fornecido em formato JSON pela TelecomX, com o objetivo de identificar padrões e variáveis relevantes para a retenção de clientes.

---

## 🧹 1. Tratamento de Dados

### ✅ 1.1 Estruturação
Extraí e organizei os seguintes blocos do JSON original:  
- `customer`  
- `account` (desmembrando `Charges` em `Charges.Monthly` e `Charges.Total`)  
- `phone`  
- `internet`  
- `Churn` (extraído do nível superior)  

### ✅ 1.2 Limpeza
- Removi espaços extras em strings  
- Normalizei capitalização (`Yes`/`No` → padrão consistente)  
- Eliminei duplicatas  
- Converti variáveis categóricas em binárias (`Yes` → `1`, `No` → `0`)  

### ✅ 1.3 Criação de variáveis auxiliares
Criei duas novas métricas:
- **`contas_diarias`**: valor diário médio (calculado como `Charges.Monthly / 30`)  
- **`qtd_servicos`**: soma de serviços ativos por cliente  

---

## 📊 2. Análise Descritiva

### 🎯 2.1 Distribuição do Churn
Identifiquei que **26,5%** dos clientes cancelaram os serviços.  
> Gerei um gráfico de barras comparando evasões vs permanências.

### 🧬 2.2 Análises específicas
Minhas principais descobertas:
- Contratos mensais têm **maior taxa de churn**  
- Combinação **Fibra Óptica + Electronic Check** mostra maior propensão a cancelamento  
- Clientes que cancelaram têm **menor tenure** (tempo como cliente)  
- **Cobranças mensais mais altas** correlacionam-se com maior churn  
- **StreamingTV** e **mais serviços contratados** reduzem evasão  

#### Visualizações que desenvolvi:
- Gráficos de barras: `Churn x Contract`, `Churn x PaymentMethod`  
- Boxplots: `tenure` e `charges_monthly` vs `churn`  
- Histograma de `contas_diarias`  
- Gráfico de dispersão: `qtd_servicos x churn`  

---

## 📈 3. Correlação entre Variáveis

### 🔍 Correlações significativas
Encontrei estas relações com `churn`:
| Variável            | Correlação |
|---------------------|------------|
| `contract_two year` | -0.30      |
| `tenure`            | -0.35      |
| `charges_monthly`   | +0.19      |

> Minha interpretação: **fidelidade (tenure) e contratos longos protegem contra churn**, enquanto cobranças mensais altas aumentam o risco.

---

## 📌 Conclusões
Com base na análise:
1. **Estratégias de retenção** devem focar em converter clientes para contratos anuais  
2. **Métodos de pagamento** digitais merecem atenção especial  
3. **Pacotes com múltiplos serviços** são eficazes para reter clientes  
4. As novas variáveis que criei (`contas_diarias`, `qtd_servicos`) mostraram-se preditivas  

---

## 🚀 Próximos Passos
Sugiro como próximas ações:
1. Desenvolver um **modelo preditivo** com as variáveis identificadas  
2. Criar **programas de fidelidade** para perfis de alto risco  
3. Implementar um **dashboard de monitoramento** contínuo  
