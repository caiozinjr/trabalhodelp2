using System;
using System.Collections.Generic;
using Mono.Data.Sqlite;


class MainClass {

   
  public static void Cadastrar(){
 
    Console.WriteLine("\n\nCadastro de Produto");
    Console.Write("Nome: ");
    string nome = Console.ReadLine();
    Console.Write("Preço: ");
    double preco = Convert.ToDouble(Console.ReadLine());
    Produto p = new Produto(nome, preco);
    p.Persistir();

  }

  public static void Listar()
  {
    Console.WriteLine("\n");
    List<Produto> produtos = Produto.ConsultarProdutos();
    foreach(var produto in produtos)
    {
      produto.Imprimir();
    }
    Console.WriteLine("======================");
    Console.WriteLine("PRESSIONE QUALQUER TECLA PARA VOLTAR");
    Console.WriteLine("======================");
  }


  public static void Procurar()
  {  
    Console.Clear();
    Console.WriteLine("======================");
    Console.WriteLine("Escreva o nome do produto de que deseja procurar");
    Console.WriteLine("======================");

    string procurar_ = Console.ReadLine();
 
    Console.Clear();
    Console.WriteLine("======================");
    Console.WriteLine("Mostrando todos os registros de: {0}", procurar_);
    Console.WriteLine("======================");
  
    List<Produto> produtos = Produto.ProcurarProdutos(procurar_);
    foreach(var produto in produtos)
    {
      produto.Imprimir();
    }
  
    Console.WriteLine("======================");
    Console.WriteLine("PRESSIONE QUALQUER TECLA PARA VOLTAR");
    Console.WriteLine("======================");
  }
 

 
    public static void Main(string[] args)
          {                 
                bool MostrarMenu = true;
                while (MostrarMenu)
                {
                    MostrarMenu = MenuPrincipal();
                }
          }




          private static bool MenuPrincipal()
            {
Console.Clear();
                Console.WriteLine("==================================================================");
                Console.WriteLine("Entre com '1' para Procurar os produtos");
                Console.WriteLine("Entre com '2' para Deletar um produto");
                Console.WriteLine("Entre com '3' para Cadastrar todos os produtos");
                Console.WriteLine("Entre com '4' para Listar um produto");
                Console.WriteLine("Entre com '5' para Fechar a aplicação");
                Console.WriteLine("==================================================================");
                switch (Console.ReadLine())
                {
                        
                        case "1":
                            Procurar();
                            Console.Read();    
                         return true;

                        case "2":
                            Deletar();
                            Console.Read();                          
                        return true;

                        case "3":
                            Produto.Cadastrar();
                            Console.Read();                          
                        return true;

                        case "4":                       
                            Listar();
                            Console.Read();   
                        return true;


                        //Close Program
                        case "5":
                           Console.Clear();
                           Console.WriteLine("======================");
                           Console.WriteLine("Terminado com sucesso!");
                           Console.WriteLine("Até breve!");
                           Console.WriteLine("======================");
                           return false;
                           

                        //DEFAULT ROUTE (BACK TO MENU)
                        default:
                            return true;



                }//END SWITCH




            }//END METHOD


}
