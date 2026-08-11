# Clube da Chef Sofia Martins

Landing page estática (HTML puro) com Meta Pixel, script de UTM (Utmify), links de checkout configurados e performance otimizada.

## Como colocar no ar (GitHub + Vercel)

### 1. Criar o repositório no GitHub
1. Acesse [github.com/new](https://github.com/new)
2. Dê um nome ao repositório (ex: `clube-chef-sofia-martins`)
3. Deixe como **Público** ou **Privado**, como preferir
4. Não marque nenhuma opção de inicialização (sem README, sem .gitignore)
5. Clique em **Create repository**

### 2. Subir os arquivos
Na página do repositório recém-criado, clique em **"uploading an existing file"** e arraste **todo o conteúdo desta pasta**, incluindo a subpasta `images/` inteira:
- `index.html`
- `vercel.json`
- `images/hero.webp`
- `images/receita-1.webp`
- `images/receita-2.webp`
- `images/receita-3.webp`
- `images/receita-4.webp`
- `README.md` (opcional)

Depois clique em **Commit changes**.

> ⚠️ Importante: a pasta `images/` precisa manter esse nome exato e estar na raiz do repositório, no mesmo nível do `index.html` — o HTML referencia as imagens como `images/hero.webp`, etc.

> Alternativa via terminal, se preferir:
> ```bash
> git init
> git add .
> git commit -m "primeira versão do site"
> git branch -M main
> git remote add origin https://github.com/SEU-USUARIO/SEU-REPOSITORIO.git
> git push -u origin main
> ```

### 3. Conectar à Vercel
1. Acesse [vercel.com/new](https://vercel.com/new)
2. Faça login com sua conta do GitHub (se ainda não tiver conectado)
3. Selecione o repositório que você acabou de criar
4. A Vercel vai detectar automaticamente que é um site estático — não precisa mudar nenhuma configuração de build
5. Clique em **Deploy**

Em cerca de 30 segundos o site estará no ar, com uma URL do tipo:
`https://seu-repositorio.vercel.app`

### 4. Domínio próprio (opcional)
Se você tiver um domínio (ex: `clubedachefsofia.com`), vá em:
**Vercel → seu projeto → Settings → Domains** e siga as instruções para apontar o DNS.

### 5. Atualizações futuras
Sempre que você editar o `index.html` (ou trocar imagens) e subir (`push`) para o GitHub, a Vercel atualiza o site automaticamente — não precisa fazer deploy manual de novo.

---

## Checklist de configuração já feita no código
- ✅ Meta Pixel (`1044850421643507`) com `PageView` automático
- ✅ Evento `InitiateCheckout` nos botões de compra
- ✅ Script UTMify (captura UTM da URL de entrada e repassa para o checkout)
- ✅ Links de checkout Hotmart configurados (Essencial, Acesso Total, Upsell)
- ✅ Layout responsivo (mobile e desktop)
- ✅ Performance otimizada: imagens extraídas do HTML e comprimidas (página caiu de ~1 MB para ~280 KB total)
- ✅ Cache de 1 ano configurado para imagens (`vercel.json`) — visitas repetidas praticamente não recarregam imagens
- ✅ `loading="lazy"` nas imagens abaixo da dobra, `preload`/`fetchpriority="high"` na imagem principal
- ✅ `preconnect` para os domínios do Meta Pixel e da Utmify, acelerando o carregamento dos scripts de tracking
- ✅ `aspect-ratio` + `width`/`height` em todas as imagens, eliminando saltos de layout durante o carregamento

## Pendências fora do código
- Configurar a **URL de destino do anúncio no Meta Ads** com os parâmetros de UTM apontando para a URL final da Vercel (ou seu domínio)
- Testar uma compra para confirmar que o evento `Purchase` (configurado na Hotmart) está disparando corretamente no Gerenciador de Eventos do Meta
