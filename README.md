# Extração e Gestão de Dados para Sistemas Web

Este script Tampermonkey foi desenvolvido para automatizar a coleta e o preenchimento de dados entre dois sites, tipicamente um sistema de gerenciamento de tickets (ITSM) e um editor de documentos. Ele simplifica o fluxo de trabalho ao permitir que o usuário extraia informações de um pedido, adicione-as a uma fila e, posteriormente, as exporte para um documento em outra página web.

**Atenção: Este código serve como uma demonstração e pode não funcionar diretamente em todos os sites.** O seu funcionamento depende muito das tags e classes HTML específicas das páginas que você pretende utilizar. Você precisará ajustar os seletores (`document.querySelector`) no código para que eles correspondam à estrutura HTML dos sites que você quer integrar.

### Funcionalidades

-   **Adicionar à Fila**: Em um site de origem (por exemplo, um sistema de tickets), o script identifica e extrai automaticamente informações como ID, data, solicitante, técnico, assunto e solução de um pedido. Com um clique, esses dados são salvos em uma fila local.
-   **Ver Fila**: Exibe um alerta com todos os pedidos atualmente salvos na fila, permitindo que você visualize os dados antes de exportá-los.
-   **Remover Próximo**: Remove o primeiro item da fila, útil para corrigir erros ou pular pedidos.
-   **Exportar Informações**: Em um site de destino (por exemplo, um editor de documentos), o script preenche os campos do documento com os dados do primeiro pedido da fila, como ID, data, solicitante, técnico e solução. Após a exportação, o pedido é automaticamente removido da fila.

### Como Usar

1.  **Instalação**: Instale o Tampermonkey (ou uma extensão similar) no seu navegador. Crie um novo script e cole o código fornecido.

2.  **Configuração**: O script foi generalizado para remover referências a sites específicos. **Antes de usar, você deve configurar os URLs nos metadados e nas constantes do código para os sites que você utiliza.**

    -   **No cabeçalho do script (`// ==UserScript==`)**:
        -   Substitua `[DOMINIO-DO-SITE-ITSM]` pelo domínio do seu sistema de tickets.
        -   Substitua `[DOMINIO-DO-EDITOR]` pelo domínio do seu editor de documentos.

    -   **No corpo do script (`(function() { ... })`)**:
        -   Substitua as strings nos `const` **`urlITSM`** e **`urlEditor`** com os mesmos domínios configurados acima.

3.  **Ajuste dos Seletores**: Para que o script funcione, você precisará inspecionar os elementos HTML das páginas de origem e destino e ajustar os seletores (`document.querySelector`) no código para corresponderem às tags e classes que você deseja extrair e preencher.

4.  **Utilização**:
    -   No seu sistema de tickets, clique no botão **"Adicionar à Fila"** para salvar os dados do pedido.
    -   No seu editor de documentos, clique em **"Exportar Info"** para preencher o documento com o primeiro pedido da fila.

---
