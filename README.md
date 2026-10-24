# Ararakú para iPhone

O jogo de `jogos.134-209-45-236.sslip.io/araraku/` (VPS, `/srv/jogos/public/araraku`) embrulhado com Capacitor 8.
Tudo roda dentro do app, sem internet. Não há Mac: a compilação e o envio acontecem no GitHub Actions (`.github/workflows/ios.yml`).

- Bilíngue: abre em inglês e, em aparelho configurado em português, em português; botões EN | PT no topo (dicionário `TXT` no `index.html`).
- A tela não rola: o tabuleiro se ajusta ao espaço livre; opções e links ficam no botão de ajustes.
- `www/` cópia do jogo (`npm run jogo` puxa de novo da VPS) · `ios/` projeto Xcode (Swift Package Manager)
- `loja/en` e `loja/pt` capturas de tela 6,9" (1320x2868) · `loja/*.html` páginas de privacidade, suporte e termos (publicadas na VPS)
- Identificador do app (não muda depois de publicado): `br.com.convivetecnologia.araraku` · Apple ID do app: `6826639497`
- Versão 1.0; o número do build é o número da execução da esteira

Atualizar o app depois de mexer no jogo: `npm run jogo` → commit → rodar a esteira → nova versão no TestFlight.

## Envio

Já feito (24/10/2026): identificador registrado, app criado na App Store Connect, chave de API e os 4 segredos no GitHub
(`APPLE_TEAM_ID`, `ASC_KEY_ID`, `ASC_ISSUER_ID`, `ASC_KEY_P8`). A conta não tem iPhone cadastrado, por isso a esteira arquiva
sem assinatura e assina para distribuição só na exportação.

- Compilar e enviar: `gh workflow run ios.yml -R cidadedigitalai/araraku-app` (ou aba Actions → Run workflow).
  O build aparece no TestFlight depois do processamento da Apple (15 a 30 min).
- Só conferir se compila, sem Apple: `gh workflow run ios.yml -R cidadedigitalai/araraku-app -f testflight=false`.
- Para mandar para revisão: preencher a página da loja abaixo nos dois idiomas, escolher o build e clicar em Enviar para revisão (1 a 3 dias).

## Página da loja

O idioma principal do app na App Store Connect é **inglês (EUA)**. O português entra em "Adicionar idioma → Português (Brasil)".
Quem tem o iPhone em português vê a página em português; o resto do mundo vê em inglês.

### English (primary)

**Name:** Ararakú
**Subtitle:** The macaw logic puzzle
**Privacy Policy URL:** https://jogos.134-209-45-236.sslip.io/araraku/privacy.html
**Support URL:** https://jogos.134-209-45-236.sslip.io/araraku/support.html
**Screenshots:** `loja/en/` (5)

**Promotional text:**
Land the macaws on the right trees, hear each one sing and watch them all fly free. A logic puzzle with the macaws of Brazil's biomes.

**Keywords:**
macaw,parrot,bird,logic,puzzle,brain,star battle,brazil,amazon,nature,educational,offline

**Description:**
Ararakú is a logic puzzle starring the macaws of Brazil.

Each color on the board is a tree, and each tree gets exactly one macaw. There can be only one macaw per row and per column, and macaws are territorial: they never perch next to each other, not even diagonally. Use logic, mark impossible squares with an X and land every macaw in the right spot.

When you get one right, the macaw blinks and sings. When the board is complete, they all fly away, free.

- Four Brazilian biomes: Pantanal, Cerrado, Amazon and Caatinga, from 5x5 to 8x8 boards
- Endless levels, each with a single solution
- Species album with facts about the Hyacinth Macaw, the Blue-and-yellow Macaw, the Red-and-green Macaw and Lear's Macaw
- Animated tutorial on first launch, plus hints, undo and auto-marking for beginners
- Music and sound effects you can turn off
- Play in English or Portuguese
- Works offline, no ads, no data collected

**App Review notes:**
Offline game, no login and no purchases. Tap marks a square with an X; double-tap lands a macaw. To see the win animation quickly, use the hint button (light bulb) and land the macaw on the highlighted square until the board is complete. The game is in English and Portuguese (EN | PT buttons at the top). An animated tutorial opens on first launch (dismiss with "Got it"; it can be replayed in Settings). Settings, privacy policy and support are in the sliders button at the top.

### Português (Brasil)

**Nome:** Ararakú
**Subtítulo:** Quebra-cabeça das araras
**URL da política de privacidade:** https://jogos.134-209-45-236.sslip.io/araraku/privacidade.html
**URL de suporte:** https://jogos.134-209-45-236.sslip.io/araraku/suporte.html
**Capturas:** `loja/pt/` (5)

**Texto promocional:**
Pouse as araras nas árvores certas, ouça cada uma cantar e veja todas voarem livres. Um quebra-cabeça de lógica com as araras dos biomas do Brasil.

**Palavras-chave:**
arara,quebra-cabeça,lógica,puzzle,pássaro,Brasil,Pantanal,Amazônia,Cerrado,Caatinga,educativo

**Descrição:**
Ararakú é um quebra-cabeça de lógica com as araras do Brasil.

Cada cor do tabuleiro é uma árvore, e cada árvore recebe exatamente uma arara. Só pode haver uma arara por linha e por coluna, e elas são territoriais: nunca pousam encostadas, nem na diagonal. Use a lógica, marque com X as casas impossíveis e pouse cada arara no lugar certo.

Quando você acerta, a arara pisca e canta. Quando o tabuleiro fica completo, todas saem voando, livres.

- Quatro biomas: Pantanal, Cerrado, Amazônia e Caatinga, do tabuleiro 5x5 ao 8x8
- Fases sem fim, todas com uma única solução
- Álbum de espécies com fatos sobre a arara-azul-grande, a arara-canindé, a arara-vermelha e a arara-azul-de-lear
- Tutorial animado na primeira vez, além de dicas, desfazer e marcação automática para quem está aprendendo
- Música e efeitos sonoros que podem ser desligados
- Jogue em português ou inglês
- Funciona sem internet, sem anúncios e sem coletar nenhum dado

## Respostas para os questionários da App Store Connect

| Onde | Pergunta | Resposta |
|---|---|---|
| Informações do app | Categoria | Jogos · subcategorias Quebra-cabeça e Educativo |
| Informações do app | Direitos de conteúdo: contém, mostra ou acessa conteúdo de terceiros? | **Não** (a ilustração da arara é do dono do app) |
| Privacidade do app | Você ou seus parceiros coletam dados deste app? | **Não** → aparece "Dados não coletados" |
| Privacidade do app | Rastreamento / identificador de publicidade | Não usa (não precisa pedir permissão de rastreamento) |
| Classificação etária | Violência, sexo, linguagem, drogas, terror, jogos de azar, concursos, tema médico | **Nenhum / Não** em tudo |
| Classificação etária | Acesso irrestrito à web, conteúdo de usuários, mensagens/chat, anúncios | **Não** em tudo → classificação **4+** |
| Classificação etária | Feito para crianças (categoria Infantil) | **Não** (fica em Jogos; a categoria Infantil exige regras extras, como portão para os pais antes de links) |
| Conformidade de exportação | Usa criptografia? | Já respondido dentro do app (`ITSAppUsesNonExemptEncryption = NÃO`); a pergunta não aparece |
| Contrato de licença | EULA | Padrão da Apple; termos complementares em `terms.html` / `termos.html` |
| Informações para a revisão | É preciso login? | **Não** (desmarcar "Login necessário") |
| Informações para a revisão | Contato | nome, telefone e e-mail de quem responde à Apple |
| Preço e disponibilidade | Preço / países | Grátis · **todos os países** |
| Lei europeia (DSA) | Status de comerciante | Para aparecer nos 27 países da União Europeia, a Apple exige declarar se você é comerciante (empresa). Se for, nome, endereço, telefone e e-mail ficam visíveis na página do app na UE. Sem a declaração, o app sai em todo o resto do mundo, menos na UE. Fica em App Store Connect → Business (Negócios) → Conformidade com a Lei de Serviços Digitais |
| Contas | Exclusão de conta | Não se aplica (o app não tem contas) |

O que já está dentro do app para a revisão: política de privacidade acessível pelo botão de ajustes ("Privacy and support", regra 5.1.1),
manifesto de privacidade `ios/App/App/PrivacyInfo.xcprivacy` (sem rastreamento, sem coleta, sem APIs de motivo obrigatório),
nenhum pedido de permissão, nenhum serviço de terceiros, idiomas declarados (`CFBundleLocalizations`: en, pt-BR) e funcionamento offline
(o jogo vem dentro do app, não é um site carregado da internet; regra 4.2).
