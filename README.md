#  🚀 Desafio SQL Xperiun - Workshop SQL

## 📊 Contexto
Este projeto faz parte do desafio SQL da plataforma Xperiun. 
O objetivo é demonstrar habilidades práticas em SQL aplicadas a um cenário de análise de vendas em uma empresa de varejo.

Imagine: o time de vendas, a diretoria e o marketing precisam de informações rápidas para tomar decisões estratégicas. Aqui entra a análise de dados! 💡

---

## 📝 Problema 1: Top 10 marcas por venda líquida em Julho/2019

O supervisor de vendas precisava de forma urgente identificar as 10 marcas com maior venda líquida no mês de julho de 2019, incluindo:
- Código da Marca
- Descrição da Marca
- Total Vendido Líquido (arredondado com duas casas decimais)

---

## 💡 Estratégia de Resolução
1. Relacionei as tabelas de Marcas, Produtos e Vendas usando **JOINs**, para combinar as informações necessárias.
2. Calculei a **venda líquida** subtraindo os descontos da venda bruta.
3. Agrupei os dados por marca para somar as vendas.
4. Ordenei os resultados do maior para o menor valor de venda líquida.
5. Limitei a consulta às 10 marcas mais vendidas.

---

## 🖥 Query SQL
```sql
-- Lista as 10 marcas com maior Venda líquida em julho/2019 
SELECT ma.Marca as Marca, 
ma.Descricao as Descricao, 
sum (v.VendaBruta - v.Desconto) as VendaLiquida 
from Marcas ma 
join Produtos p 
on ma.Marca = p.Marca 
join Vendas v 
on v.Produto = p.Produto 
where v.Movimento 
between '2019-07-01' and '2019-07-31' 
group by ma.Marca , ma.Descricao 
order by VendaLiquida DESC 
limit 10
```

---

## Resultado Esperado
A query retorna as 10 marcas com maior venda líquida no mês de julho de 2019, permitindo ao supervisor de vendas tomar decisões rápidas e informadas.

---

## ✨ Aprendizados
- Prática de JOINs múltiplos para combinar tabelas diferentes.
- Cálculo de métricas financeiras simples (venda líquida).
- Filtragem e ordenação de dados para análises rápidas.
- Documentação do processo de pensamento, facilitando a leitura por outras pessoas ou equipes.

Este exercício reforçou minha capacidade de transformar dados brutos em informações estratégicas para tomada de decisão.


![Desafio 1](problema1.png)

