# Atividade-PDS
Cotrole Bibliotecário - linguagem de porgramação Python
class Livro:
    def __init__(self, titulo, autor, genero, quantidade):
        self.titulo = titulo
        self.autor = autor
        self.genero = genero
        self.quantidade = quantidade

class Biblioteca:
    def __init__(self):
        self.livros = []
        self.registro = []

    def cadastrar_livro(self, titulo, autor, genero, quantidade):
        livro = Livro(titulo, autor, genero, quantidade)
        self.livros.append(livro)
        self.registro.append(f"Cadastro - Título: {titulo}")

    def buscar_livro(self, titulo):
        for livro in self.livros:
            if livro.titulo == titulo:
                return livro
        return None

    def buscar_genero(self, genero):
        livros_genero = []
        for livro in self.livros:
            if livro.genero == genero:
                livros_genero.append(livro)
        return livros_genero

    def atualizar_estoque(self, titulo, quantidade):
        livro = self.buscar_livro(titulo)
        if livro:
            livro.quantidade += quantidade
            self.registro.append(f"Atualizacaoo de estoque - Titulo: {titulo}, Quantidade: {quantidade}")

    def registro_atividade(self):
        for atividade in self.registro:
            print(atividade)

    def relatorio_bibliotecario(self):
        for livro in self.livros:
            print(f"Titulo: {livro.titulo}, Autor: {livro.autor}, Genero: {livro.genero}, Quantidade: {livro.quantidade}")


# Exemplo de uso do controle bibliotecario
biblioteca = Biblioteca()

biblioteca.cadastrar_livro("Harry Potter", "J.K. Rowling", "Fantasia", 5)
biblioteca.cadastrar_livro("1984", "George Orwell", "Ficcao Cientifica", 3)

livro_encontrado = biblioteca.buscar_livro("1984")
if livro_encontrado:
    print(f"Livro encontrado: {livro_encontrado.titulo}")
else:
    print("Livro nao encontrado")

livros_fantasia = biblioteca.buscar_genero("Fantasia")
print("Livros de Fantasia:")
for livro in livros_fantasia:
    print(f"Titulo: {livro.titulo}, Autor: {livro.autor}")

biblioteca.atualizar_estoque("Harry Potter", 2)

biblioteca.registro_atividade()

print("Relatorio Bibliotecario:")
biblioteca.relatorio_bibliotecario()
