# Permaneo

Frontend demonstrativo em React, Vite e JavaScript, baseado no [Permaneo Remodelagem no Figma](https://www.figma.com/design/He18eTo0fKiaZ5qGJy0Aj0/Permaneo-Remodelagem?node-id=0-1).

## Executar no VS Code

Requer Node.js 20.19 ou superior e npm. No terminal:

```bash
git clone --branch feat/figma-platform-complete https://github.com/Caique2347/DemoDay-Permaneo.git
cd DemoDay-Permaneo
npm install
npm run dev
```

Abra a pasta `DemoDay-Permaneo` no VS Code e acesse a URL exibida pelo Vite, normalmente `http://localhost:5173`. Não abra `index.html` diretamente pelo explorador de arquivos.

```bash
npm run build
npm run preview
npm test
```

Os testes utilizam o Chrome instalado no computador, em modo headless. Iniciam seu próprio servidor na porta 5174. Capturas de celular, tablet e computador ficam em `test-results/`, fora do versionamento.

## Telas e navegação

React Router gerencia rotas com hash, permitindo hospedagem estática sem configuração de fallback no servidor.

| Perfil | Telas |
| --- | --- |
| Público | Home, proposta, funcionamento, perfis, soluções e acesso demonstrativo |
| Direção e coordenação | Painel da escola, acompanhamento, carômetro, perfis de estudantes, notificações, relatórios e configurações |
| Professor | Minhas turmas, registro de frequência, acompanhamento, carômetro das turmas, perfis, notificações e configurações |
| Estudante | Meu painel, pedido de apoio e Meu espaço |

As telas possuem versões clara e escura. A preferência de tema é aplicada antes da montagem do React e preservada no navegador. Os exemplos de estudantes, indicadores e gráficos são fictícios.

## Organização

```text
src/
  components/  Controles e formulários reutilizáveis, JSX e CSS Module na mesma pasta
  pages/       Telas do Figma, cada JSX junto de seu CSS Module
  routes/      Registro de telas e carregamento sob demanda
  data/        Dados demonstrativos
  hooks/       Persistência local
  styles/      Reset, tipografia, fontes locais e variáveis dos temas
  imagens/     Fotografias, logos e assets SVG locais do Figma
```

Os identificadores `data-node-id` e `data-name` permitem rastrear elementos de volta ao Figma. Não há TypeScript nem URLs temporárias de imagens em execução. Fontes Manrope e Sora e fotografias são servidas localmente.

## Interações e armazenamento

- Seleção de perfil, navegação, tema, menus e acesso demonstrativo identificado.
- Busca, filtros combinados, alternância de cartões/lista, paginação e abertura de perfis no carômetro.
- Cadastro local de aluno com iniciais ou fotografia, turma e responsável; os cartões são adicionados à grade.
- Registro local de frequência, acompanhamento e pedidos de apoio.
- Categorias e marcação de leitura de notificações demonstrativas, exportação CSV e configurações locais.
- Modais com fechamento por Escape, retorno de foco e contenção da navegação por Tab.

Os dados são armazenados em `localStorage` com prefixo `permaneo-`. Para reiniciar a demonstração, limpe o armazenamento deste site nas ferramentas do navegador. Dados de demonstração não são compartilhados entre dispositivos. Fotografias locais têm limite de 2 MB; a capacidade total depende do armazenamento do navegador.

## Dependências de backend e limites

O acesso não autentica contas reais. A navegação por perfil organiza a demonstração; autorização e proteção de dados devem ser implementadas no servidor antes do uso em produção.

Persistência em banco de dados, matrícula real, sincronização dos indicadores, validação das permissões, recuperação de senha, envio de mensagens e notificações, câmeras e reconhecimento facial dependem de backend e integrações. Os gráficos preservam os valores demonstrativos do Figma e não recalculam indicadores institucionais a partir dos cadastros locais. Alguns atalhos do protótipo apresentam apenas contexto demonstrativo.

## Validação

`npm test` verifica 29 rotas nos dois temas, carregamento das imagens locais, seleção e entrada por perfil, busca, abertura de perfil, cadastro, persistência após recarregar, console e layouts em 390, 768 e 1440 pixels. Também confere ausência de TypeScript, URLs temporárias e o pareamento JSX/CSS Module.

As capturas são evidências de renderização; não constituem comparação automatizada pixel a pixel com o Figma.
