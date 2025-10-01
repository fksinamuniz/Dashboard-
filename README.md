Estrutura do Projeto: Dashboard de Saúde Pública - Parauapebas/PA
Visão Geral
O projeto é um dashboard interativo para visualização de indicadores de saúde do município de Parauapebas, no estado do Pará. O dashboard consolida dados de múltiplas fontes (IBGE, PEC, SIA, SIM, etc.) e os apresenta de forma categorizada, com filtros e abas para facilitar a navegação.

Tecnologias Utilizadas
HTML5: Estrutura da página.

CSS3: Estilização, com uso de Grid e Flexbox para layout responsivo.

JavaScript (ES6): Funcionalidades interativas, filtros, e consumo de API do IBGE.

Estrutura de Arquivos
text
dashboard-saude-parauapebas/
│
├── index.html (arquivo principal)
├── style.css (estilos - atualmente no mesmo arquivo HTML)
└── script.js (javascript - atualmente no mesmo arquivo HTML)
Funcionalidades
1. Cabeçalho com Identificação Institucional
Logo da Prefeitura de Parauapebas (representada por emoji e texto).

Título do dashboard e descrição.

Timestamp com a última atualização (atualizado a cada minuto).

2. Seção de Filtros
Filtro por Categoria (IBGE, APS, MAC, Redes).

Filtro por Subcategoria (dinâmico, baseado na categoria selecionada).

Filtro por Fonte de Dados (PEC, IBGE, SIA, etc.).

Filtro por Data (data de referência do indicador).

Busca por texto (em tempo real, com debounce).

Botão para limpar todos os filtros.

3. Sistema de Abas
Visão Geral: Apresenta um resumo com os principais indicadores e depois separa por categorias.

População (IBGE): Indicadores demográficos.

Atenção Primária (APS): Indicadores de atenção primária.

Média e Alta Complexidade (MAC): Indicadores de média e alta complexidade.

Redes de Atenção / Integração: Indicadores de redes de saúde.

4. Cards de Indicadores
Cada indicador é exibido em um card com:

Subcategoria (tag colorida).

Nome do indicador.

Ícone representativo.

Valor (com destaque).

Unidade de medida.

Fonte e data de referência.

Efeitos de hover e animações.

5. Indicadores de Tendência
Seta para cima (melhora), para baixo (piora) ou estável.

Cores: verde (melhora), vermelho (piora), laranja (estável).

6. Responsividade
Layout adaptável para desktop, tablet e mobile.

Menu de abas vira horizontal e scrollable em telas menores.

7. Integração com API do IBGE
Busca automática da população estimada de Parauapebas.

Atualização do card de população com dados em tempo real.

Fallback para valor estático em caso de erro.

Estrutura de Dados
Array de Indicadores
Cada indicador é um objeto com as seguintes propriedades:

javascript
{
  id: 'populacao', // opcional, usado para atualização dinâmica
  categoria: "IBGE",
  subcategoria: "População",
  indicador: "População estimada",
  valor: "305.771",
  unidade: "habitantes",
  fonte: "IBGE",
  icon: "👥",
  data: "2025",
  tendencia: "up" // "up", "down", "stable"
}
Fontes de Dados
IBGE: Dados demográficos.

PEC: Programa de Enfrentamento à Covid-19.

SIA: Sistema de Informações Ambulatoriais.

SIM: Sistema de Informações sobre Mortalidade.

SAI: Sistema de Acompanhamento de Indicadores.

SAMU: Serviço de Atendimento Móvel de Urgência.

HGP: Hospital Geral de Parauapebas.

DIRCA: Diretoria de Regulação, Controle e Avaliação.

Fluxo de Funcionalidades
Inicialização
Atualiza o timestamp.

Carrega os indicadores (com dados estáticos e busca da população via API).

Renderiza a visão geral.

Filtragem
O usuário seleciona filtros (categoria, subcategoria, fonte, data) ou digita na busca.

O evento dispara a função filtrarIndicadores (com debounce na busca).

Os indicadores são filtrados e a view é atualizada.

Navegação por Abas
O usuário clica em uma aba.

A função switchTab é chamada, que:

Remove a classe active de todas as abas.

Adiciona active na aba clicada.

Renderiza o conteúdo correspondente.

Atualização da População (API)
A função buscarPopulacaoIBGE é chamada na inicialização.

Faz uma requisição à API do SIDRA/IBGE (tabela 6579, código do município 1505536).

Atualiza o indicador de população e re-renderiza se necessário.

Personalização e Manutenção
Adicionar Novos Indicadores
Basta adicionar um novo objeto no array indicadores, seguindo a estrutura definida.

Modificar Estilos
Os estilos estão no mesmo arquivo HTML, na tag <style>. É possível extrair para um arquivo CSS externo.

Modificar Fontes de Dados
Para alterar a API da população, modifique a função buscarPopulacaoIBGE.

Para adicionar novas fontes, inclua no filtro de fonte e nos indicadores.

Considerações de Performance
Uso de debounce na busca para evitar múltiplas renderizações.

Cache de elementos DOM para melhor performance.

Animações CSS otimizadas.

Compatibilidade
Navegadores modernos (Chrome, Firefox, Safari, Edge).

Responsivo para mobile e tablet.

Possíveis Expansões
Gráficos e visualizações mais elaboradas.

Exportação de relatórios.

Mais integrações com APIs de saúde.

Sistema de login para diferentes níveis de acesso.

Este documento serve como um guia completo para entender, manter e expandir o projeto.

PROMPT: Estrutura Completa do Projeto Dashboard de Saúde Pública
📋 VISÃO GERAL DO PROJETO
Nome do Projeto: Dashboard de Saúde Pública - Parauapebas/PA
Objetivo: Sistema de visualização e monitoramento de indicadores de saúde do município
Público-Alvo: Gestores públicos, profissionais de saúde, pesquisadores e população em geral
Tecnologias: HTML5, CSS3, JavaScript (ES6+), APIs REST
Status: Em produção - Versão 1.0

🏗️ ARQUITETURA TÉCNICA
Estrutura de Arquivos
text
dashboard-saude-parauapebas/
│
├── index.html                      # Arquivo principal
├── assets/
│   ├── css/
│   │   └── style.css              # Estilos (atualmente inline)
│   ├── js/
│   │   └── script.js              # JavaScript (atualmente inline)
│   ├── img/
│   │   ├── logo-prefeitura.png    # Logo oficial
│   │   └── favicon.ico            # Ícone do site
│   └── data/
│       └── indicadores.json       # Base de dados (opcional)
│
└── README.md                       # Documentação
Stack Tecnológico
Frontend: HTML5 semântico, CSS3 com Grid/Flexbox, JavaScript vanilla

APIs: IBGE SIDRA (dados populacionais)

Design: Responsivo, Mobile-First

Performance: Debounce, Cache DOM, Lazy Loading

🎨 SISTEMA DE DESIGN
Paleta de Cores
css
/* Cores Principais */
--primary-color: #667eea           /* Azul principal */
--secondary-color: #764ba2         /* Roxo secundário */
--accent-ibge: #f56565            /* Vermelho - IBGE */
--accent-aps: #48bb78             /* Verde - APS */
--accent-mac: #ed8936             /* Laranja - MAC */
--accent-redes: #9f7aea           /* Roxo - Redes */
--text-primary: #000000           /* Preto - Texto principal */
--text-secondary: #4a5568         /* Cinza - Texto secundário */
--background: #f8fafc             /* Cinza claro - Fundo */
Tipografia
Fonte Principal: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif

Hierarquia:

Títulos: 2.5rem (h1), 1.5rem (h2), 1.1rem (h3)

Corpo: 0.95rem - 1.1rem

Pequeno: 0.8rem - 0.9rem

Componentes de UI
Header: Logo + Título + Timestamp

Filtros: Grid responsivo de controles

Tabs System: Navegação vertical/horizontal

Cards: Indicadores com hover effects

Overview: Visão geral com métricas principais

📊 ESTRUTURA DE DADOS
Schema dos Indicadores
javascript
{
  id: string,                     // Identificador único
  categoria: "IBGE" | "Atenção Primária (APS)" | "Média e Alta Complexidade (MAC)" | "Redes de Atenção / Integração",
  subcategoria: string,           // e.g., "População", "Cobertura", "Consultas"
  indicador: string,              // Nome completo do indicador
  valor: string,                  // Valor formatado (e.g., "305.771", "89.4%")
  unidade: string,                // Unidade de medida
  fonte: "IBGE" | "PEC" | "SIA" | "SIM" | "SAI" | "SAMU" | "HGP" | "DIRCA",
  icon: string,                   // Emoji representativo
  data: string,                   // Data de referência (YYYY-MM-DD)
  tendencia: "up" | "down" | "stable"  // Direção da tendência
}
Categorias e Subcategorias
text
IBGE:
  ↳ População

Atenção Primária (APS):
  ↳ Cobertura
  ↳ Quantidade de ACS
  ↳ Quantidade de Equipes
  ↳ Consultas
  ↳ Atendimentos
  ↳ Programas Específicos
  ↳ Doenças Crônicas
  ↳ Prevenção
  ↳ Inovação

Média e Alta Complexidade (MAC):
  ↳ Regulação
  ↳ Especialidades
  ↳ Exames
  ↳ Internação
  ↳ Urgência/Emergência

Redes de Atenção / Integração:
  ↳ Saúde Mental (RAPS)
  ↳ Saúde da Mulher/Criança
  ↳ Urgência
🔧 FUNCIONALIDADES PRINCIPAIS
1. Sistema de Filtros
javascript
// Filtros disponíveis
- Categoria (dropdown)
- Subcategoria (dinâmico)
- Fonte de dados (dropdown)
- Período (date picker)
- Busca textual (input text)
- Limpeza de filtros (botão)
2. Navegação por Abas
javascript
// Abas disponíveis
- 📈 Visão Geral (overview)
- 📊 População (IBGE) (ibge)
- 🏡 Atenção Primária (APS) (aps)
- 🏥 Média e Alta Complexidade (mac)
- 🔗 Redes de Atenção (redes)
3. Integração com APIs
javascript
// API IBGE - População
Endpoint: https://apisidra.ibge.gov.br/values/t/6579/n6/1505536
Código Município: 1505536 (Parauapebas)
Tabela: 6579 (Estimativa populacional)
4. Responsividade
css
/* Breakpoints */
- Desktop: > 1024px
- Tablet: 768px - 1024px
- Mobile: < 768px
🚀 FLUXO DE EXECUÇÃO
Inicialização
DOM Content Loaded

Atualizar timestamp

Inicializar subcategorias

Buscar dados população (API IBGE)

Renderizar visão geral

Atualizar estatísticas

Filtragem em Tempo Real
Event Listeners em todos os filtros

Debounce na busca (300ms)

Aplicar filtros combinados

Atualizar view baseado na aba atual

Mostrar/ocultar estados (loading, sem resultados)

Navegação entre Abas
Clique na aba → switchTab()

Remover active de todos

Adicionar active ao selecionado

Renderizar conteúdo específico

📱 COMPONENTES DETALHADOS
Header Component
html
<div class="header-top">
  <div class="logo-container">
    <div class="logo-img">🏛️</div>
    <div class="logo-text">
      <div class="prefeitura">PREFEITURA DE PARAUAPEBAS</div>
      <div class="slogan">Um novo tempo, uma nova história</div>
      <div class="secretaria"><strong>SEMSA</strong> - Secretaria Municipal de Saúde</div>
    </div>
  </div>
  <div class="header-title">
    <h1>🏥 Dashboard de Saúde Pública</h1>
    <p>Parauapebas - Pará | Indicadores e Métricas de Saúde Baseados em Dados Reais</p>
  </div>
</div>
Filter Component
html
<div class="filters-grid">
  <!-- 5 filtros + botão limpar -->
  <div class="filter-group">[Categoria]</div>
  <div class="filter-group">[Subcategoria]</div>
  <div class="filter-group">[Fonte]</div>
  <div class="filter-group">[Data]</div>
  <div class="filter-group">[Busca]</div>
  <div class="filter-group">[Limpar]</div>
</div>
Card Components
html
<!-- Card de Indicador -->
<div class="indicator-card categoria-ibge">
  <div class="card-subcategory">População</div>
  <div class="card-header">...</div>
  <div class="card-value">305.771</div>
  <div class="card-unit">habitantes</div>
  <div class="card-source">Fonte: IBGE | 2025</div>
</div>

<!-- Card de Visão Geral -->
<div class="overview-card">
  <div class="overview-icon">👥</div>
  <div class="overview-title">População estimada</div>
  <div class="overview-value">305.771</div>
  <div class="overview-unit">habitantes</div>
  <div class="trend-indicator trend-up">↗️ Tendência</div>
</div>
🔄 ESTADOS DA APLICAÇÃO
Loading State
html
<div class="loading-state show">
  <div class="spinner"></div>
  <p>Carregando indicadores de saúde...</p>
</div>
Empty State
html
<div class="no-results show">
  <div class="no-results-icon">🔍</div>
  <h3>Nenhum indicador encontrado</h3>
  <p>Tente ajustar os filtros para encontrar os indicadores desejados.</p>
</div>
Error State (API)
javascript
// Fallback para erro na API IBGE
.catch(err => {
  console.error('Erro ao buscar dados do IBGE:', err);
  // Usar valor estático como fallback
  indicadorPopulacao.valor = "305.771";
  indicadorPopulacao.data = "2025";
});
🎯 FUNÇÕES PRINCIPAIS
Core Functions
javascript
// 1. Gerenciamento de Estado
let dadosFiltrados = [...indicadores];
let abaAtual = 'overview';
let searchTimeout;

// 2. Funções Principais
updateTimestamp()              // Atualiza relógio
switchTab(tabId, element)      // Troca de aba
filtrarIndicadores()           // Aplica filtros
renderizarIndicadores()        // Renderiza cards
renderizarVisaoGeral()         // Renderiza overview
buscarPopulacaoIBGE()          // API IBGE
clearAllFilters()              // Limpa filtros
atualizarSubcategorias()       // Subcategorias dinâmicas
atualizarEstatisticasFiltros() // Stats de filtros
Utility Functions
javascript
criarCardIndicador(indicador)     // Template do card
criarCardVisaoGeral(indicador)    // Template overview
criarSecaoCategoria()             // Template seção
formatarData(dataString)          // Formata datas
debounce(func, wait)              // Otimização performance
📈 PERFORMANCE E OTIMIZAÇÃO
Técnicas Implementadas
Debounce Search: 300ms delay na busca

DOM Caching: Elementos cacheados em domElements

Event Delegation: Listeners eficientes

CSS Transforms: Animações performáticas

Lazy Rendering: Renderização sob demanda

Métricas Alvo
First Contentful Paint: < 1.5s

Time to Interactive: < 3s

Lighthouse Score: > 90

Mobile Performance: Otimizado

🔒 CONSIDERAÇÕES DE ACESSIBILIDADE
Features Implementadas
✅ Navegação por teclado (Tab/Enter)

✅ Contraste adequado (fonte preta)

✅ Labels semânticos nos formulários

✅ ARIA labels implícitas

✅ Textos alternativos para ícones

Melhorias Futuras
Screen reader compatibility

High contrast mode

Keyboard navigation enhancements

🌐 INTEGRAÇÕES E APIs
API IBGE SIDRA
javascript
const codMunicipio = 1505536; // Parauapebas
const url = `https://apisidra.ibge.gov.br/values/t/6579/n6/${codMunicipio}`;

// Response Structure
{
  "D2N": "2025",              // Ano
  "V": "305771",              // Valor numérico
  // ... outros campos
}
Estrutura de Resposta
A API retorna array de objetos com dados históricos, onde o último elemento é o ano mais recente.

📋 CHECKLIST DE IMPLEMENTAÇÃO
✅ Concluído
Estrutura HTML semântica

Sistema de design responsivo

Navegação por abas

Sistema de filtros completo

Integração com API IBGE

Estados de loading/error

Performance optimizations

Acessibilidade básica

🔄 Em Desenvolvimento
Exportação de dados

Gráficos e visualizações

Sistema de favoritos

Modo offline

PWA capabilities

🚀 INSTRUÇÕES DE IMPLANTAÇÃO
Desenvolvimento
bash
# 1. Clone ou baixe o projeto
# 2. Abra index.html em servidor local
python -m http.server 8000
# ou
npx serve .
Produção
bash
# 1. Hospedar em servidor web estático
# 2. Configurar HTTPS (para APIs)
# 3. Configurar CORS se necessário
# 4. Monitorar performance
Variáveis de Ambiente (Futuro)
javascript
// config.js
const CONFIG = {
  IBGE_API_URL: 'https://apisidra.ibge.gov.br/values',
  MUNICIPIO_CODE: '1505536',
  CACHE_TIMEOUT: 3600000 // 1 hora
};
📞 SUPORTE E MANUTENÇÃO
Monitoramento
Console errors (JavaScript)

API response times

User interactions analytics

Mobile usage statistics

Atualizações Regulares
Dados populacionais (anual)

Indicadores de saúde (mensal)

Manutenção de APIs

Security patches
