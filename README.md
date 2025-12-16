## 📄 Verificação Facial em Tempo Real (Real-Time Face Verification)

Este projeto implementa um sistema de verificação facial simples em tempo real usando a biblioteca **Face-API.js**, que utiliza modelos de Machine Learning (ML) leves e otimizados para rodar diretamente no navegador (browser). O objetivo é comparar a face detectada na câmera com uma face de referência predefinida (`referencia.jpg`).

---

### ✨ Funcionalidades

* **Detecção Facial em Tempo Real:** Identifica a localização de faces no *stream* de vídeo da câmera.
* **Extração de Descritores:** Gera vetores de características (descritores) para cada face detectada.
* **Comparação e Verificação:** Compara os descritores da face da câmera com o descritor da face de referência.
* **Indicação Visual:** Desenha caixas delimitadoras coloridas no canvas (**verde** para Match, **vermelho** para Desconhecido).
* **Responsividade:** O layout é ajustável para diferentes tamanhos de tela.

### ⚙️ Tecnologias Utilizadas

* **HTML5/CSS3:** Estrutura e estilização da interface.
* **JavaScript:** Lógica principal de controle da câmera e do Face-API.js.
* **Face-API.js:** Biblioteca JavaScript que fornece modelos de ML para detecção e reconhecimento facial.

---

### 🚀 Como Rodar o Projeto

Devido às restrições de segurança do navegador (CORS Policy) ao carregar os modelos de Machine Learning e acessar a câmera, **é obrigatório rodar este projeto em um servidor web local**.

#### 1. Pré-requisitos

* **Node.js** e **npm** instalados (ou qualquer servidor local, como Python Simple HTTP Server).

#### 2. Configuração

1.  Clone este repositório:
    ```bash
    git clone [SEU_REPO_URL]
    cd [pasta_do_projeto]
    ```

2.  **Adicione a Imagem de Referência:**
    Você deve adicionar um arquivo de imagem chamado exatamente `referencia.jpg` (ou `.png`) na raiz do projeto, contendo a face que você deseja reconhecer/verificar.

3.  **Inicie o Servidor Local (Exemplo com Node/NPM):**

    Se você não tiver um servidor local preferido, pode instalar o `http-server`:
    ```bash
    npm install -g http-server
    http-server
    ```

    Alternativamente, se estiver usando Python 3:
    ```bash
    python -m http.server 8000
    ```

#### 3. Acesso

* Abra seu navegador e navegue para o endereço exibido pelo servidor (geralmente `http://localhost:8080` ou `http://127.0.0.1:8000`).
* Permita o acesso à câmera quando solicitado.

---

### 📘 Detalhes Técnicos e Ajustes

#### Tolerância (Threshold)

A variável `DISTANCE_THRESHOLD` no JavaScript controla o quão próxima (baixa) a distância entre os descritores deve ser para que um *match* seja considerado válido:

```javascript
const DISTANCE_THRESHOLD = 0.6; // Ajuste conforme a necessidade de precisão
 ```
**Valores típicos:**

0.6: Bom equilíbrio entre precisão e tolerância (padrão).

0.4 ou menos: Aumenta a precisão (menos falsos positivos), mas pode falhar mais facilmente com variações de ângulo/iluminação.

0.7 ou mais: Aumenta a tolerância, mas pode levar a mais falsos positivos (reconhecer pessoas diferentes).

**Resolução e Performance**
O Face-API.js faz os cálculos de detecção usando a resolução nativa do stream da câmera. No entanto, o projeto foi ajustado para garantir que a visualização na tela seja responsiva usando a propriedade offsetWidth / offsetHeight do elemento de vídeo, evitando problemas de caixas delimitadoras desalinhadas em telas menores.

**🤝 Contribuição**
Sinta-se à vontade para abrir issues ou pull requests para melhorias no código, na performance ou no design.
