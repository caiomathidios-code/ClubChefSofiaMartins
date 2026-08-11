# Clube da Chef Sofia Martins

## Deploy (GitHub + Vercel)
1. Crie um repositório novo no GitHub.
2. Suba TODO o conteúdo desta pasta (index.html, vercel.json, README.md e a pasta images/ inteira) mantendo essa mesma estrutura, na raiz do repositório.
3. Vá em vercel.com/new, conecte o repositório e clique em Deploy.
4. Pronto — o link estará no ar em segundos.

## O que foi corrigido nesta versão
- Imagens extraídas do HTML e comprimidas em WebP: página caiu de ~1 MB para ~280 KB.
- Testado e confirmado (screenshot real via navegador) que todas as imagens carregam corretamente, sem distorção.
- `loading="lazy"` nas imagens abaixo da dobra, `fetchpriority="high"` na imagem principal.
- `aspect-ratio` + `width`/`height` em todas as imagens — sem saltos de layout.
- Cache de 1 ano configurado para as imagens.
- Sem nenhum script de reload/refresh no código — o "refresh forçado" era causado pelo peso de 1MB+ do HTML antigo (imagens embutidas), já eliminado.

## Atualização — otimização mobile (imagens)
- **Corrigida a troca de fotos das receitas**: as legendas "Arroz Doce", "Pão Integral" e "Sopa da Pedra" estavam apontando para as fotos erradas (ex.: a foto de sopa aparecia com o título "Arroz Doce"). Cada foto agora corresponde ao prato certo.
- Todas as fotos dos cards foram recortadas em quadrado (1:1) centralizado, exatamente no formato em que aparecem na tela — elimina bytes de pixels que antes eram baixados e depois cortados pelo navegador.
- Cada imagem agora tem **duas resoluções** (300px e 520px para as receitas, 480px e 900px para a imagem principal) servidas via `srcset`/`sizes`, para que o celular baixe a versão pequena e o desktop a versão grande — nunca mais peso desnecessário.
- Resultado: no celular, o peso total das imagens caiu de ~244 KB para **~145 KB** (redução de ~40%). No desktop, ~283 KB.
- **Atualização:** o formato AVIF foi removido. Ele é mais leve, mas alguns navegadores embutidos de apps (Instagram, Facebook, WebViews Android mais antigos) — comuns em tráfego vindo de anúncios — dizem suportar AVIF mas falham ao decodificar, mostrando a imagem corrompida/quebrada. Ficamos só com WebP, que tem suporte universal e ainda é bem mais leve que JPEG/PNG.
- Todos os nomes de arquivo agora descrevem o prato (`receita-bacalhau-*`, `receita-arroz-doce-*`, `receita-pao-integral-*`, `receita-sopa-pedra-*`, `hero-*`), facilitando manutenção futura.
