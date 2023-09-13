# Cuenta-Bancaria
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApplication1
{   
    class Program
    {
        static void Main(string[] args)
        {
            CuentaVista tm = new CuentaVista();
            //Crear menu
            string menu = "\tBienvenia a tu Cajero Automatico\n";
            menu += "1.- Retirar monto\n";
            menu += "2.- Depositar monto\n";
            menu += "3.- Consultar saldo\n";
            menu += "4.- Cambiar clave\n";
            menu += "5.- Salir";

            do
            {
                Console.WriteLine(menu);
                string menuOpciones = Console.ReadLine();
                switch (menuOpciones)
                {
                    case "1":
                        Console.Write("Ingrese el monto: ");
                        tm.Retiro(Convert.ToInt32(Console.ReadLine()));
                        Console.Write("Tu saldo actual es: ");
                        Console.Write(tm.Saldo);
                        break;
                    case "2":
                        Console.Write("Ingrese deposito: ");
                        tm.Deposito(Convert.ToInt32(Console.ReadLine()));
                        Console.Write("Tu saldo actual es de: " + tm.Saldo);
                        break;
                    case "3":
                        Console.WriteLine(tm.Mensage());
                        break;
                    case "4":
                        Console.WriteLine("Ingrese su clave nueva");
                        int nuevaClave;
                        nuevaClave = Convert.ToInt32(Console.ReadLine());
                        if (nuevaClave == tm.Clave){
                            Console.WriteLine("NO SE PUEDE REPETIR LA MISMA CLAVE");
                        }
                        else
                        {
                            tm.Clave = nuevaClave;
                        }
                        break;
                    
                    default:
                        return;

                        
                }

            } while (true);

           
        }

    }

    public class CuentaVista
    {
        private string rut;
        private int clave;
        private int saldo;

        public CuentaVista()
        {
            rut = "1-9";
            clave = 1515;
            saldo = 1000000;
        }

        public int Clave { get { return clave; } set { clave = value; } }
        public int Saldo { get { return saldo; } }
        public string Rut { get { return rut; } }

        public string Mensage()
        {
            string mensaje = "Tu saldo de cuenta es: " + saldo;
            return mensaje;
        }
        public void Retiro(int retiro)
        {
            saldo -= retiro;
        }
        public void Deposito(int deposito)
        {
            saldo += deposito;
        }

    }
}
