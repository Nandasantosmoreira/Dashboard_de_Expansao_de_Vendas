
# 📊 Dashboard de Expansão de Vendas

![grafico](https://github.com/user-attachments/assets/6ef844a2-e7b1-4e91-a1bd-2e1f6aa5703c)

## 📌 Descrição do Projeto

Este dashboard foi desenvolvido para acompanhar a **expansão de vendas no estado**, permitindo a análise de KPIs como **faturamento**, **margem bruta**, **ticket médio** e **cobertura de clientes/cidades** ao longo do tempo. Com ele, é possível comparar periodicamente o desempenho e identificar tendências de crescimento.

## 📂 Estrutura do Projeto

- 📁 `dataset/` - Contém os arquivos de dados (se aplicável)
- 📁 `measures/` - Medidas DAX utilizadas no Power BI
- 📁 `visuals/` - arquivo background FIGMA
- 📁 `docs/` - Documentação do projeto
- 📁 `powerbi-file/` - Arquivo `.pbix` do Power BI

## 🔗 Modelagem e Relacionamentos

### 📑 Tabelas Principais

| Tabela        | Descrição                                     |
| ------------- | --------------------------------------------- |
| `fVendas`     | Fato principal com todas as vendas realizadas |
| `dCliente`    | Dimensão de clientes, incluindo categorias    |
| `dProduto`    | Dimensão de produtos, categorias e preços     |
| `dVendedor`   | Dimensão de vendedores e regiões              |
| `dCalendario` | Dimensão de tempo                             |

### 🔗 Relacionamentos

- `fVendas[cdCliente]` → `dCliente[cdCliente]`
- `fVendas[cdProduto]` → `dProduto[cdProduto]`
- `fVendas[cdVendedor]` → `dVendedor[cdVendedor]`
- `fVendas[Data]` → `dCalendario[Data]`

## 📊 Principais Indicadores

| Indicador                   | Descrição                                        |
| --------------------------- | ------------------------------------------------ |
| **Faturamento**             | Soma do total vendido                            |
| **Margem Bruta %**          | (Lucro Bruto / Faturamento) \* 100               |
| **Ticket Médio**            | Faturamento / Número de clientes                 |
| **Cobertura Clientes 6M**   | Número de clientes nos últimos 6 meses           |
| **Cobertura Cidades 6M**    | Número de cidades com vendas nos últimos 6 meses |
| **Variação de Faturamento** | Crescimento percentual entre períodos            |

## 📈 Visuais do Dashboard

### 1️⃣ Faturamento por Cidade

**Descrição:** Exibe o faturamento segmentado por cidades.

### 2️⃣ Evolução de Vendas nos Últimos 6 Meses

**Descrição:** Demonstra a evolução do faturamento ao longo do tempo.

## 🛠 Medidas DAX

### 📌 Variação de Vendas 6M

```DAX
VAR VendasAtual =
    CALCULATE([Faturamento], DATESINPERIOD(dCalendario[Data], MAX(dCalendario[Data]), -6, MONTH))

VAR VendasAnterior =
    CALCULATE([Faturamento], DATESINPERIOD(dCalendario[Data], MAX(dCalendario[Data]) - 12, -6, MONTH))

RETURN
    DIVIDE(VendasAtual - VendasAnterior, VendasAnterior, 0)
```

**Explicação:** Calcula a variação percentual entre os últimos 6 meses e o mesmo período do ano anterior.

## 🔄 Atualizações Futuras

✅ Implementar previsão de vendas\
✅ Melhorar o desempenho das medidas DAX\
✅ Criar um dashboard mobile-friendly

## 🚀 Como Utilizar

1. Baixar o arquivo `.pbix` e abrir no Power BI Desktop.
2. Atualizar os dados conectando-se ao banco ou arquivo EXCEL.
3. Explorar as análises aplicando filtros interativos.

> **Requisitos:** Power BI Desktop instalado.

## 📞 Contato

📧 Email: [fernandasm.vitoria@hotmail.com](mailto\:fernandasm.vitoria@hotmail.com)\
📌 LinkedIn: fernanda-santos-moreira-analista-python-r-sql\
