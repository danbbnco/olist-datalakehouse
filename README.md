# 🛒 Olist Data Lakehouse

Projeto de portfólio construído em Databricks com Delta Lake, simulando uma arquitetura de Data Lakehouse moderna baseada em dados públicos da Olist.

A estrutura segue boas práticas profissionais, inspirada na trilha **"Lago do Mago"** do TeoMeWhy, com adaptações realistas para ambiente gratuito.

---

## 🎯 Objetivo

Construir um Data Lakehouse completo com Databricks + PySpark, estruturado em camadas (RAW → BRONZE → SILVER → GOLD), simulando ingestões full e CDC, e finalizando com visualizações em Power BI.

---

## ⚙️ Tecnologias e Ferramentas

- Apache Spark (PySpark)
- Delta Lake
- Databricks (Unity Catalog)
- Git + GitHub
- Power BI
- Dados públicos da [Olist no Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)

---

## 🏗️ Arquitetura

```

RAW (full_load / cdc) → BRONZE → SILVER → GOLD


```

**RAW**: organização por domínio funcional (`comercial`, `clientes`, `produtos`), separando `full_load` e `cdc` em volumes.

**BRONZE**: ingestão tratada em Delta Lake, sem uso de volumes como destino (gerenciado pelo Unity Catalog).

**SILVER e GOLD**: transformações e agregações (em progresso).

---

## 📁 Estrutura de Dados (Unity Catalog)

#### 📚 Catálogo: `olist`

#### 🔹 Schemas:
- `raw_comercial`
- `raw_clientes`
- `raw_produtos`
- `bronze`
- `silver`
- `gold`

#### 📦 Volumes (dentro de schemas `raw_*`):

```
olist.raw_comercial.full_load.orders/
olist.raw_comercial.full_load.order_items/
olist.raw_comercial.full_load.payments/
olist.raw_comercial.full_load.sellers/

olist.raw_clientes.full_load.customers/
olist.raw_clientes.full_load.geolocation/
olist.raw_clientes.full_load.reviews/

olist.raw_produtos.full_load.products/
olist.raw_produtos.full_load.category_translation/
```

#### 🔸 CDC:
Volumes `cdc` já criados, mas ainda não utilizados — serão ativados futuramente com dados simulados.

---

## ✅ Progresso

- [x] Repositório criado e conectado via Repos.
- [x] Estrutura de catálogo, schemas e volumes criada.
- [x] Upload dos arquivos full_load em volumes organizados.
- [x] Ingestão da camada RAW para BRONZE (com Delta Lake e `saveAsTable`).
- [ ] Simulação de CDC e uso de MERGE.
- [ ] Ingestão e transformação na camada SILVER.
- [ ] Agregações e KPIs na camada GOLD.
- [ ] Visualização final em Power BI.
- [ ] Finalização e publicação da documentação.

---

## 📜 Notebooks

Organizados dentro da pasta `src/` por camada:

```
src/
├── bronze/
│   └── ingestao_comercial.ipynb
│   └── ingestao_clientes.ipynb
│   └── ingestao_produtos.ipynb
├── silver/
│   └── (em breve)
├── gold/
│   └── (em breve)
```

---

## 📌 Observações

- A ingestão incremental via CDC será adicionada posteriormente.

---

## 📝 Licença

MIT © 2025 Daniel Bibanco
