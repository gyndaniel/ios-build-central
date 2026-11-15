# 🍏 ios-build-central

Repositório central de automação e compilação de aplicativos **Apple iOS (Swift e SwiftUI)** usando **GitHub Actions**.

Este repositório funciona como uma "fábrica central de build". Qualquer outro projeto ou workspace seu pode utilizar esta estrutura sem precisar configurar uma máquina Mac do zero.

---

## 🚀 Como usar em qualquer projeto / workspace

Em qualquer projeto novo de aplicativo iOS no seu GitHub, adicione apenas o arquivo `.github/workflows/compilar.yml` na raiz do seu projeto com o seguinte conteúdo:

```yaml
name: Compilar para iPhone

on:
  push:
    branches: [ main, master ]
  workflow_dispatch: # Permite disparar manualmente com 1 clique na aba Actions

jobs:
  compilar:
    uses: gyndaniel/ios-build-central/.github/workflows/ios-pipeline.yml@main
    with:
      scheme_name: 'MeuApp' # Substitua pelo nome do seu App / Scheme
      configuration: 'Release'
```

---

## 📦 O que esta pipeline faz:

1. Inicia uma máquina virtual **macOS oficial da Apple** com processador Apple Silicon (M-series) e Xcode atualizado.
2. Resolve dependências do **Swift Package Manager (SPM)** automaticamente.
3. Compila o código fonte em **Swift / SwiftUI nativo**.
4. Gera o arquivo de instalação **`.ipa`**.
5. Publica o instalador na aba **Artifacts** da execução para você baixar diretamente no seu computador ou celular.
