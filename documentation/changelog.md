<p align="center">
 <img src="images/OitiHeader.png"/>
</p>

# Changelog

### [Versão 1.0.1](https://github.com/oititec/android-oiti-sdk-versions/releases/tag/1.0.1)

Data: 03/10/2025

- Atualização da FaceTec [9.7.87]
  - Melhorias na acurácia e compatibilidade do 3D Liveness (animações e transições mais suaves em diversos dispositivos).
  - APIs novas pra customizar tempo de exibição das animações no fluxo de Liveness (display time configurável entre 1,5 s e 3 s).
  - Remoção das APIs de timeout de sessão de Liveness não operacionais, deixando o SDK mais limpo.
  - Segurança de Liveness reforçada com testes de injeção de vídeo Nível 4 e 5 pra mitigar ameaças de IA Generativa.

### [Versão 1.0.0](https://github.com/oititec/android-oiti-sdk-versions/releases/tag/1.0.0)

Data: 10/09/2025

- Nova arquitetura modular, construída do zero para substituir as soluções legadas.
- Suporte a Jetpack Compose para criação de interfaces modernas, flexíveis e customizáveis.
- Integração com múltiplos providers de verificação:
  - FaceTec (9.7.83)
  - iProov (10.3.2)
- Abstração unificada para consumo simplificado de providers, preparada para futuras extensões.