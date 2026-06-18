<p align="center">
 <img src="images/OitiHeader.png"/>
</p>

# Changelog

### [Versão 1.2.0](https://github.com/oititec/android-oiti-sdk-versions/releases/tag/1.2.0)

Data: 18/06/2026

### FaceTec
- Refatoração da arquitetura
- Novas opções de tema (retry, result screen, activity indicator)
- Fix: dark mode, textos, ofuscação.
- FaceTec: 9.7.126

### Design System
- Novo scaffold com suporte a system bars/insets
- Telas de liveness (FaceTec/iProov) refatoradas
- Correções na tela de resultado do iProov

### [Versão 1.1.0](https://github.com/oititec/android-oiti-sdk-versions/releases/tag/1.1.0)

Data: 18/12/2025

### Atualizações
- FaceTec SDK atualizado para a versão 9.7.102

### Mudanças importantes

#### Possibilidade de pular a tela de instruções.

```kotlin
setInstructionsTheme {
    setShowInstructionScreen(false)
}
```

#### Alteração no parâmetro de seleção de provider de liveness.

Antes:
```kotlin
CertifaceSDK.createLivenessManager(CertifaceSDK.LivenessProvider.IPROOV)
```

Depois:
```kotlin
CertifaceSDK.createLivenessManager(LivenessProvider.IPROOV)
```

#### Nova forma de customizar totalmente os fluxos utilizando functions composables.

#### Exemplo FaceTec:
```kotlin
FacetecTheme.build {
    setCustomScreens(
        FacetecCustomScreensBuilder.build {
            setCustomInstructionComposable { callbacks ->
                FacetecInstructionScreen(
                    onStartClick = callbacks.onStartClick,
                    onBack = callbacks.onBack
                )
            }

            setCustomPermissionComposable { callbacks ->
                FacetecPermissionScreen(
                    onPermissionGranted = callbacks.onPermissionGranted,
                    onBack = callbacks.onBack
                )
            }

            setCustomLoadingDialogComposable { message, progress ->
                FacetecLoadingDialog(
                    message = message,
                    progress = progress
                )
            }
        }
    )
}
```

#### Exemplo IProov:
```kotlin
IProovTheme.build {
    setCustomScreens(
        IProovCustomScreensBuilder.build {
            setCustomInstructionComposable { callbacks ->
                IProovInstructionScreen(
                    onStartClick = callbacks.onStartClick,
                    onBack = callbacks.onBack
                )
            }

            setCustomPermissionComposable { callbacks ->
                IProovPermissionScreen(
                    onPermissionGranted = callbacks.onPermissionGranted,
                    onBack = callbacks.onBack
                )
            }

            setCustomLoadingDialogComposable { message, progress ->
                IProovLoadingDialog(
                    message = message,
                    progress = progress
                )
            }

            setCustomResultComposable { resultState ->
                IProovResultScreen(
                    success = resultState.success,
                    errorMessage = resultState.errorMessage,
                    showRetryButton = resultState.showRetryButton,
                    reason = resultState.reason,
                    onRetry = resultState.onRetry
                )
            }
        }
    )
}
```

---

### [Versão 1.0.3](https://github.com/oititec/android-oiti-sdk-versions/releases/tag/1.0.3)

Data: 18/11/2025

**Atualizações de SDKs e ajustes internos**
- Atualizações de versões
  - FaceTec SDK atualizado para 9.7.96
  - iProov SDK atualizado para 11.1.0
- Mudanças importantes
  - Removido o parâmetro setCamera do fluxo iProov devido às alterações introduzidas na versão 11.1.0.
  - O controle de câmera agora é totalmente interno ao SDK.
  - Ajustes internos de segurança e melhorias de fluxo foram aplicados para acompanhar as mudanças da nova versão do iProov.

---

### [Versão 1.0.2](https://github.com/oititec/android-oiti-sdk-versions/releases/tag/1.0.2)

Data: 30/10/2025

### **Adicionado**
- **LineDrawing Filter**
  - Suporte a **background** e **foreground** personalizados.
  - Exemplo:
    ```kotlin
    setFilter(
        FilterTheme.LineDrawing(
            style = LineDrawingStyle.SHADED,
            background = "#32a852".toColorInt(),
            foreground = "#4232a8".toColorInt()
        )
    )
    ```

- **Close Button**
  - Nova propriedade adicionada para personalizar a cor do botão de fechamento:
    ```kotlin
    setCloseButtonColor("#a8324a")
    ```

### **Alterado**
- **Instructions Screen / DomainInstructionCustomsBuilder**
 - Refatoração de nomenclatura das propriedades relacionadas às instruções de **liveness**:
    - `documentTypesInstruction*` → `firstInstruction*`
    - `documentTipsInstruction*` → `secondInstruction*`
  - O comportamento das propriedades permanece o mesmo, apenas com nomes atualizados para melhor clareza e padronização.
  - Exemplo:
    ```kotlin
    // Antes
    setDocumentTypesInstructionIcon(R.drawable.arrow_left_black)
    setDocumentTipsInstructionIcon(R.drawable.camera_alt)

    // Agora
    setFirstInstructionIcon(R.drawable.arrow_left_black)
    setSecondInstructionIcon(R.drawable.camera_alt)
    ```

### **Atualizado**
- **iProov SDK** atualizado para a versão **10.4.0**.
  - Novas propriedades disponíveis apenas para o modo **Genuine Presence Assurance (GPA)**:
    - `controlXPosition`: exibe mensagem para movimentar o rosto **horizontalmente**.
    - `controlYPosition`: exibe mensagem para movimentar o rosto **verticalmente**.
    - `scanningPrompts`: exibe mensagens de *“scaneando”* e *“scaneado”* durante o processo.
   
---

### [Versão 1.0.1](https://github.com/oititec/android-oiti-sdk-versions/releases/tag/1.0.1)

Data: 03/10/2025

- Atualização da FaceTec [9.7.87]
  - Melhorias na acurácia e compatibilidade do 3D Liveness (animações e transições mais suaves em diversos dispositivos).
  - APIs novas pra customizar tempo de exibição das animações no fluxo de Liveness (display time configurável entre 1,5 s e 3 s).
  - Remoção das APIs de timeout de sessão de Liveness não operacionais, deixando o SDK mais limpo.
  - Segurança de Liveness reforçada com testes de injeção de vídeo Nível 4 e 5 pra mitigar ameaças de IA Generativa.

---

### [Versão 1.0.0](https://github.com/oititec/android-oiti-sdk-versions/releases/tag/1.0.0)

Data: 10/09/2025

- Nova arquitetura modular, construída do zero para substituir as soluções legadas.
- Suporte a Jetpack Compose para criação de interfaces modernas, flexíveis e customizáveis.
- Integração com múltiplos providers de verificação:
  - FaceTec (9.7.83)
  - iProov (10.3.2)
- Abstração unificada para consumo simplificado de providers, preparada para futuras extensões.
