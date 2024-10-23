# CONTA ABSTRATA
Exercício da AC2 sobre conta abstrata

## 🚀 Enunciado

Crie a classe abstrata ContaBancaria que possui os métodos abstratos, saque, depósito e consulta.

A partir dela derivam as classes concretas ContaCorrente e ContaPoupança.

A ContaPoupança não permite saques maiores que o saldo. Já a ContaCorrente possui um limite após o saldo se esgotar.

As duas contas possuem diferentes taxas para saque, depósito e consulta.


### 📋 Código

package ContaBancaria;


abstract class ContaBancaria { //Começo criando a classe abstrata que irá fornecer a estrutura basíca para as demais classes que irão derivar dela
    protected double saldo;

    public ContaBancaria(double saldo) {
        this.saldo = saldo;
    }

    public abstract boolean saque(double valor); //O método retorna um valor do tipo boolean, que pode ser true ou false.
    public abstract void deposito(double valor); //Este método executa uma ação que no caso é, fazer um depósito
    public abstract void consulta(); //E esse método é utilizado para exibir informações, como o saldo da conta.
}

class ContaCorrente extends ContaBancaria { //A primeira classe que deriva, com suas propriedades no caso o limite, taxa do saque e taxa do deposito
    private double limite;
    private double taxaSaque = 2.0;
    private double taxaDeposito = 1.0;

    public ContaCorrente(double saldo, double limite) {
        super(saldo);
        this.limite = limite;
    }

    @Override
    public boolean saque(double valor) { //Retorna o valor, indicando que o saque foi bem-sucedido ou que não foi permitido pois excedeu o limite
        if (valor > saldo + limite) {
            System.out.println("Saque não permitido. Excede o limite.");
            return false;
        }
        saldo -= (valor + taxaSaque);
        System.out.println("Saque de R$" + valor + " realizado. Saldo atual: R$" + saldo);
        return true;
    }

    @Override
    public void deposito(double valor) {  //Retorna o valor, indicando que o deposito foi bem-sucedido somando com o saldo já existem na conta
        saldo += (valor - taxaDeposito);
        System.out.println("Depósito de R$" + valor + " realizado. Saldo atual: R$" + saldo);
    }

    @Override
    public void consulta() { //Mostra o valor consultado com base no saldo
        System.out.println("Saldo atual: R$" + saldo);
    }
}

class ContaPoupanca extends ContaBancaria { //Segunda classe que deriva, com suas propiedades no caso taxa de saque e depósito
    private double taxaSaque = 1.0;
    private double taxaDeposito = 0.5;

    public ContaPoupanca(double saldo) {
        super(saldo);
    }

    @Override
    public boolean saque(double valor) { //Retorna o valor, indicando que o saque foi bem-sucedido ou que não foi permitido pois excedeu o limite
        if (valor > saldo) {
            System.out.println("Saque não permitido. Saldo insuficiente.");
            return false;
        }
        saldo -= (valor + taxaSaque);
        System.out.println("Saque de R$" + valor + " realizado. Saldo atual: R$" + saldo);
        return true;
    }

    @Override
    public void deposito(double valor) { //Retorna o valor, indicando que o deposito foi bem-sucedido somando com o saldo já existem na conta
        saldo += (valor - taxaDeposito);
        System.out.println("Depósito de R$" + valor + " realizado. Saldo atual: R$" + saldo);
    }

    @Override
    public void consulta() {  //Mostra o valor consultado com base no saldo
        System.out.println("Saldo atual: R$" + saldo);
    }



    public static void main(String[] args) {  //Criação de duas contas, uma bancária e outra poupança e mostrando como irá ficar
        ContaBancaria contaCorrente = new ContaCorrente(1000, 500);
        ContaBancaria contaPoupanca = new ContaPoupanca(500);

        System.out.println("Conta Corrente:");
        contaCorrente.consulta();
        contaCorrente.deposito(200);
        contaCorrente.saque(1200);
        contaCorrente.consulta();

        System.out.println("\nConta Poupança:");
        contaPoupanca.consulta();
        contaPoupanca.deposito(100);
        contaPoupanca.saque(700);
        contaPoupanca.consulta();
    }
    }


### 🔧 Instalação

* Explicação de como deve ser utilizado o projeto

## 🛠️ Construído com

Ferramentas utilizadas e bibliotecas

* IDE Eclipse

## 📌 Versão

* **Versão 1.0** caso seja atualizado manter a descrição inicial e inserir uma nova linha com descrição da atualização.
* **Versão 1.1** - *Refatoração* *data 09/09/24*

## ✒️ Autores

* João Carlos Ferreira de Araujo RA 248152 - AC2 de Programação Orientada à Objetos

