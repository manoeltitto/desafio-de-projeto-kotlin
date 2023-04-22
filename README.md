# desafio-de-projeto-kotlin
Desafio de Projeto desenvolvido através do template 'Aprenda Kotlin com exemplos-lab"

https://pl.kotl.in/vm4ssuEKV

enum class Nivel { BASICO, INTERMEDIARIO, DIFICIL }

class Usuario(val nome: String, var formacao: Formacao? = null)

data class ConteudoEducacional(var nome: String, val duracao: Int = 60)

data class Formacao(val nome: String, var conteudos: List<ConteudoEducacional>) {

    val inscritos = mutableListOf<Usuario>()

    fun matricular(usuario: Usuario) {
        usuario.formacao = this
        inscritos.add(usuario)
    }
}

fun main() {
    val usuario1 = Usuario("Manoel")
    val usuario2 = Usuario("Pereira")
    val usuario3 = Usuario("Titto")

    val conteudo1 = ConteudoEducacional("Introdução ao Kotlin", 120)
    val conteudo2 = ConteudoEducacional("Programação Orientada a Objetos", 180)
    val conteudo3 = ConteudoEducacional("Banco de Dados Relacional", 240)

    val formacao1 = Formacao("Desenvolvimento de Software", listOf(conteudo1, conteudo2, conteudo3))
    val formacao2 = Formacao("Análise de Dados", listOf(conteudo3, conteudo1))
    val formacao3 = Formacao("Desenvolvimento Web", listOf(conteudo2, conteudo3))

    formacao1.matricular(usuario1)
    formacao2.matricular(usuario2)
    formacao3.matricular(usuario3)

    println("${usuario1.nome}, Matriculado em: ${usuario1.formacao?.nome}")
    println("${usuario2.nome}, Matriculado em: ${usuario2.formacao?.nome}")
    println("${usuario3.nome}, Matriculado em: ${usuario3.formacao?.nome}")
}

