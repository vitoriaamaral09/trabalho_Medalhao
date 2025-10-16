# Como usar

### Passos para visualizar a documentação localmente

1. Abra o terminal na pasta do projeto:

   ```bash
   cd trabalho_medalhao
   ```

2. Crie e ative um ambiente virtual:

   ```bash
   python3 -m venv venv
   source venv/bin/activate  # no macOS/Linux
   ```

3. Instale o MkDocs e o tema Material:

   ```bash
   pip install mkdocs mkdocs-material
   ```

4. Rode o site localmente:

   ```bash
   mkdocs serve
   ```

5. Abra no navegador:

   [http://127.0.0.1:8000](http://127.0.0.1:8000)

6. Para publicar no GitHub Pages:

   ```bash
   mkdocs gh-deploy
   ```
