# Ararakú para iPhone

O jogo de `jogos.134-209-45-236.sslip.io/araraku/` (VPS, `/srv/jogos/public/araraku`) embrulhado com Capacitor 8.
Tudo roda dentro do app, sem internet. Não há Mac: a compilação e o envio acontecem no GitHub Actions (`.github/workflows/ios.yml`).

- `www/` cópia do jogo (`npm run jogo` puxa de novo da VPS) · `ios/` projeto Xcode (Swift Package Manager)
- `loja/` capturas de tela 6,9" (1320x2868) prontas para a App Store Connect
- Identificador do app (não muda depois de publicado): `br.com.convivetecnologia.araraku`
- Versão 1.0; o número do build é o número da execução da esteira

Atualizar o app depois de mexer no jogo: `npm run jogo` → commit → rodar a esteira → nova versão no TestFlight.

## O que só o dono da conta faz (uma vez)

1. **Conta de desenvolvedor Apple** — developer.apple.com/programs/enroll (US$ 99/ano, Apple ID com verificação em 2 etapas).
   Pessoa física: aparece seu nome na loja, aprova em 1 a 2 dias. Empresa: aparece o nome da empresa, exige número D-U-N-S e demora mais.
2. **Registrar o identificador** — developer.apple.com/account → Certificates, Identifiers & Profiles → Identifiers → **+** → App IDs → App →
   Bundle ID explícito `br.com.convivetecnologia.araraku`, descrição `Araraku`.
3. **Criar o app** — appstoreconnect.apple.com → Apps → **+** Novo app → iOS, nome `Ararakú`, idioma principal Português (Brasil),
   o bundle ID acima, SKU `araraku`.
4. **Chave de API** — App Store Connect → Usuários e acesso → Integrações → App Store Connect API → Chaves da equipe → gerar com acesso **Admin**
   (a assinatura automática cria o certificado de distribuição e precisa desse nível).
   Baixar o `AuthKey_XXXXXXXXXX.p8` (só dá para baixar uma vez) e anotar o **Key ID** e o **Issuer ID**.
   O **Team ID** fica em developer.apple.com/account → Membership details.
5. **Segredos no GitHub** (no terminal; o `.p8` nunca vai para o repositório):
   ```
   gh secret set APPLE_TEAM_ID -R cidadedigitalai/araraku-app
   gh secret set ASC_KEY_ID    -R cidadedigitalai/araraku-app
   gh secret set ASC_ISSUER_ID -R cidadedigitalai/araraku-app
   gh secret set ASC_KEY_P8    -R cidadedigitalai/araraku-app < caminho/AuthKey_XXXXXXXXXX.p8
   ```
6. **Compilar e enviar** — `gh workflow run ios.yml -R cidadedigitalai/araraku-app` (ou aba Actions → Run workflow).
   O build aparece no TestFlight depois do processamento da Apple (15 a 30 min). Testar no próprio iPhone pelo app TestFlight.
7. **Enviar para revisão** — preencher a página da loja com os textos abaixo e as capturas de `loja/`, e clicar em Enviar para revisão (1 a 3 dias).

## Página da loja (pt-BR)

**Nome:** Ararakú
**Subtítulo:** Quebra-cabeça das araras
**Categoria:** Jogos · subcategorias Quebra-cabeça e Educativo
**Preço:** grátis · **Classificação etária:** 4+ (responder "nenhum" em tudo)
**Privacidade do app:** Dados não coletados
**URL de privacidade e de suporte:** https://jogos.134-209-45-236.sslip.io/araraku/privacidade.html
**Direitos de conteúdo:** o app não usa conteúdo de terceiros (a ilustração da arara é do dono do app)

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
- Dicas, desfazer e marcação automática para quem está aprendendo
- Música e efeitos sonoros que podem ser desligados
- Funciona sem internet, sem anúncios e sem coletar nenhum dado

**Notas para a revisão da Apple:**
Jogo offline, sem login e sem compras. Toque marca uma casa com X; toque duplo pousa a arara. Para ver a animação de vitória rapidamente, use o botão de dica (lâmpada) e pouse a arara na casa destacada até completar o tabuleiro.
