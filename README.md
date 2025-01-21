# Programação Orientada a Objetos (POO)

A **Programação Orientada a Objetos (POO)** é um paradigma de programação que organiza o código em objetos, que são instâncias de classes. Ela busca organizar o código de forma mais eficiente e modular. A POO é baseada em quatro pilares principais: **Abstração**, **Encapsulamento**, **Herança** e **Polimorfismo**.

## Pilares da POO

### 1. **Abstração**

A abstração é o processo de simplificação de um problema, focando apenas nos aspectos essenciais e ocultando os detalhes desnecessários. Em termos práticos, isso significa que você pode criar uma classe que representa um conceito ou objeto do mundo real e, em vez de se preocupar com todos os detalhes internos, você foca apenas nos aspectos que são importantes para a tarefa em questão.

**Exemplo de Abstração:**

```tsx
class Carro {
  cor: string;
  marca: string;
  modelo: string;
  ano: number;
  potencia: number;

  constructor(
    cor: string,
    marca: string,
    modelo: string,
    ano: number,
    potencia: number
  ) {
    this.cor = cor;
    this.marca = marca;
    this.modelo = modelo;
    this.ano = ano;
    this.potencia = potencia;
  }

  ligar(): void {
    console.log(`${this.modelo} está ligado!`);
  }
}
```

### 2. **Encapsulamento**

Encapsulamento é o processo de proteger os dados de um objeto, expondo apenas as informações necessárias e ocultando as implementações internas. Isso é feito através de **modificadores de acesso** como `public`, `private`, `protected`, entre outros.

**Exemplo de Encapsulamento:**

```tsx
class Carro {
  private cor: string; // Atributo privado, não acessível fora da classe
  public marca: string;
  public modelo: string;
  public ano: number;

  constructor(cor: string, marca: string, modelo: string, ano: number) {
    this.cor = cor;
    this.marca = marca;
    this.modelo = modelo;
    this.ano = ano;
  }

  public obterCor(): string {
    return this.cor; // Método público para acessar a cor, mantendo a privacidade do atributo
  }
}

const carro = new Carro("preto", "Volkswagen", "Fusca", 1970);
console.log(carro.obterCor()); // 'preto'
```

### 3. **Herança**

Herança permite que você crie uma nova classe baseada em uma classe existente. A nova classe herda os atributos e métodos da classe original e pode adicionar ou modificar comportamentos.

**Exemplo de Herança:**

```tsx
class Veiculo {
  marca: string;
  modelo: string;
  ano: number;

  constructor(marca: string, modelo: string, ano: number) {
    this.marca = marca;
    this.modelo = modelo;
    this.ano = ano;
  }

  ligar(): void {
    console.log(`${this.modelo} está ligado!`);
  }
}

class Carro extends Veiculo {
  potencia: number;

  constructor(marca: string, modelo: string, ano: number, potencia: number) {
    super(marca, modelo, ano); // Chama o construtor da classe base (Veiculo)
    this.potencia = potencia;
  }

  acelerar(): void {
    console.log(`${this.modelo} está acelerando!`);
  }
}

const meuCarro = new Carro("Volkswagen", "Fusca", 1970, 90);
meuCarro.ligar(); // Método herdado da classe Veiculo
meuCarro.acelerar(); // Método da classe Carro
```

### 4. **Polimorfismo**

O polimorfismo permite que um mesmo método tenha comportamentos diferentes dependendo do contexto. Isso é possível porque uma classe pode sobrescrever um método da classe pai, ou uma classe pode ter vários métodos com o mesmo nome, mas com parâmetros diferentes.

**Exemplo de Polimorfismo:**

```tsx
class Veiculo {
  ligar(): void {
    console.log("O veículo está ligado.");
  }
}

class Carro extends Veiculo {
  ligar(): void {
    console.log("O carro está ligado.");
  }
}

class Moto extends Veiculo {
  ligar(): void {
    console.log("A moto está ligada.");
  }
}

function ligarVeiculo(veiculo: Veiculo): void {
  veiculo.ligar(); // O comportamento varia dependendo do tipo do veículo
}

const carro = new Carro();
const moto = new Moto();

ligarVeiculo(carro); // "O carro está ligado."
ligarVeiculo(moto); // "A moto está ligada."
```

## Como iniciar um projeto com Node.js e TypeScript

1. **Inicializar o projeto**:

```bash
npm init -y

```

1. **Instalar dependências**:

```bash
npm install typescript ts-node

```

1. **Criar o arquivo `tsconfig.json`**:

```bash
npx tsc --init

```

1. **Configurações no `tsconfig.json`**:

Dentro do arquivo `tsconfig.json`, configure:

```json
{
  "target": "es2022",
  "outDir": "./dist"
}
```

## Exemplo de Classe em TypeScript

Aqui está um exemplo simples de uma classe `Carro` usando TypeScript:

```tsx
type TCarro = {
  cor: string;
  marca: string;
  modelo: string;
  ano: number;
  potencia?: number;
};

class Carro {
  cor: string;
  marca: string;
  modelo: string;
  ano: number;
  potencia: number;

  constructor(carro: TCarro) {
    this.cor = carro.cor;
    this.marca = carro.marca;
    this.modelo = carro.modelo;
    this.ano = carro.ano;
    this.potencia = carro.potencia ?? 90;
  }

  mostrarDetalhes(): void {
    console.log(`${this.marca} ${this.modelo} - ${this.ano}`);
  }
}

const novoCarro = {
  cor: "Preto",
  marca: "Volkswagen",
  modelo: "Fusca",
  ano: 1970,
  potencia: 120,
};

const fusca = new Carro(novoCarro);
fusca.mostrarDetalhes(); // Exibe: Volkswagen Fusca - 1970
```

## Conclusão

A Programação Orientada a Objetos é uma abordagem poderosa para organizar e estruturar o código, oferecendo uma maneira intuitiva de modelar problemas do mundo real. Com os conceitos de **Abstração**, **Encapsulamento**, **Herança** e **Polimorfismo**, você pode criar sistemas modulares, reutilizáveis e fáceis de manter.
