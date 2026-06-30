# Mapa — Unidades Dispensadoras de PEP · PrEP · TARV (SES-DF)

Visualização cartográfica interativa das **69 unidades de saúde** que dispensam
profilaxias e tratamento para o HIV no Distrito Federal — Profilaxia Pós-Exposição
(**PEP**), Profilaxia Pré-Exposição (**PrEP**) e Tratamento Antirretroviral (**TARV**).

> Fonte: Diretoria de Assistência Farmacêutica — Secretaria de Estado de Saúde do
> Distrito Federal (SES-DF). Versão 04/2025.

## 🗺️ Os cinco mapas temáticos

| # | Mapa | Descrição |
|---|------|-----------|
| 01 | **Cobertura por Serviço** | Cada unidade como anéis concêntricos (PEP / PrEP / TARV), com camadas que podem ser isoladas. |
| 02 | **Tipo de Unidade** | Símbolos categorizados pela natureza do estabelecimento (UBS, UPA, Emergência, Policlínica…). |
| 03 | **Densidade da Rede** | Mapa de calor da concentração espacial da oferta, ponderado pelo nº de serviços. |
| 04 | **Síntese por Região de Saúde** | Limites administrativos oficiais agregados nas 7 Regiões de Saúde. Apenas RAs com unidade ficam coloridas. |
| 05 | **Cobertura da Rede** | Todas as UBS, UPA, Hospitais e Policlínicas do DF (base oficial SES-DF), comparando dispensadoras confirmadas vs. candidatas não confirmadas — visão de cobertura potencial. |

Recursos: troca de base cartográfica (claro / satélite), grade de coordenadas,
escala gráfica, rosa-dos-ventos, *popups* por unidade e legenda dinâmica.

## 🚀 Publicar no GitHub Pages

1. Crie um repositório no GitHub e envie **o conteúdo desta pasta** para a raiz
   (ou para uma pasta `docs/`).

   ```bash
   git init
   git add .
   git commit -m "Mapa de unidades PEP/PrEP/TARV - SES-DF"
   git branch -M main
   git remote add origin https://github.com/SEU-USUARIO/SEU-REPO.git
   git push -u origin main
   ```

2. No repositório, vá em **Settings → Pages**.
3. Em *Build and deployment → Source*, escolha **Deploy from a branch**.
4. Selecione a branch `main` e a pasta `/ (root)` (ou `/docs`, se usou essa pasta).
5. Salve. Em ~1 minuto a página estará no ar em
   `https://SEU-USUARIO.github.io/SEU-REPO/`.

> O arquivo `.nojekyll` já está incluído para o GitHub servir os arquivos sem
> processamento do Jekyll.

## 📁 Estrutura

```
.
├── index.html            # Página principal (abre direto no navegador)
├── support.js            # Runtime de renderização
├── data/
│   ├── units.js          # 69 unidades dispensadoras (módulo ES usado pela página)
│   ├── units.json        # Mesmos dados em JSON puro (reuso/integração)
│   ├── cobertura.js      # 197 UBS/UPA/Hospital/Policlínica do DF (universo candidato), com flag de dispensação
│   ├── cobertura.json    # Mesmos dados em JSON puro
│   └── regioes.js        # Limites das Regiões Administrativas por Região de Saúde
├── .nojekyll
├── LICENSE
└── README.md
```

## 🧩 Tecnologia

- [Leaflet](https://leafletjs.com/) 1.9.4 + [Leaflet.heat](https://github.com/Leaflet/Leaflet.heat) para o mapa interativo.
- Camadas de base: © OpenStreetMap / © CARTO e Esri World Imagery.
- Limites administrativos: [geodata-distrito-federal-brasil](https://github.com/caefleury/geodata-distrito-federal-brasil) (SIRGAS 2000 / EPSG:4674).
- Fontes: Archivo e IBM Plex Mono (Google Fonts).

> É necessário acesso à internet para carregar os *tiles* do mapa, as bibliotecas
> e as fontes (servidos por CDN).

## ⚠️ Observações

- Nas Unidades Básicas de Saúde (UBS), a dispensação na PEP é apenas do esquema
  preferencial ARV: Tenofovir/Lamivudina (TDF/3TC) 300/300 mg + Dolutegravir (DTG)
  50 mg ao dia.
- As coordenadas das 69 unidades dispensadoras foram conferidas na base oficial
  do GeoServer SES-DF (Sala de Situação) sempre que disponível (56 de 69); as
  13 unidades ausentes nessa base foram validadas manualmente via Google Places
  (campo `fonte_geo` em `units.json` indica a origem de cada coordenada).
- No Mapa 05, a base de cobertura (197 unidades) vem integralmente do GeoServer
  oficial; "dispensa" marca correspondência exata com uma das 69 unidades
  confirmadas, "candidata" indica mesmo tipo de estabelecimento sem confirmação.
- No Mapa 04, somente as Regiões Administrativas que possuem ao menos uma unidade
  dispensadora aparecem coloridas; as demais são exibidas em cinza.

## 📄 Licença

Código sob licença [MIT](LICENSE). Dados de saúde são de domínio público,
de autoria da SES-DF — mantenha os créditos à fonte.
