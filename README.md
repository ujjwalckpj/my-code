using System;

namespace GarmentSimulator
{
    // The abstract factory interface that declares methods for creating abstract products
    public interface IGarmentFactory
    {
        ITop CreateTop();
        IPants CreatePants();
        IShoes CreateShoes();
    }

    // The abstract product interface that declares the common behavior of all tops
    public interface ITop
    {
        void Wear();
    }

    // The abstract product interface that declares the common behavior of all pants
    public interface IPants
    {
        void Wear();
    }

    // The abstract product interface that declares the common behavior of all shoes
    public interface IShoes
    {
        void Wear();
    }

    // A concrete factory class that implements the abstract factory interface and creates professional garment products
    public class ProfessionalGarmentFactory : IGarmentFactory
    {
        public ITop CreateTop()
        {
            return new Shirt();
        }

        public IPants CreatePants()
        {
            return new Trousers();
        }

        public IShoes CreateShoes()
        {
            return new FormalShoes();
        }
    }

    // A concrete factory class that implements the abstract factory interface and creates casual garment products
    public class CasualGarmentFactory : IGarmentFactory
    {
        public ITop CreateTop()
        {
            return new TShirt();
        }

        public IPants CreatePants()
        {
            return new Jeans();
        }

        public IShoes CreateShoes()
        {
            return new Sneakers();
        }
    }

    // A concrete factory class that implements the abstract factory interface and creates party garment products
    public class PartyGarmentFactory : IGarmentFactory
    {
        public ITop CreateTop()
        {
            return new Dress();
        }

        public IPants CreatePants()
        {
            return new Skirt();
        }

        public IShoes CreateShoes()
        {
            return new Heels();
        }
    }

    // A concrete product class that implements the abstract product interface and defines the specific behavior of a shirt
    public class Shirt : ITop
    {
        public void Wear()
        {
            Console.WriteLine("Wearing a shirt.");
        }
    }

    // A concrete product class that implements the abstract product interface and defines the specific behavior of a t-shirt
    public class TShirt : ITop
    {
        public void Wear()
        {
            Console.WriteLine("Wearing a t-shirt.");
        }
    }

    // A concrete product class that implements the abstract product interface and defines the specific behavior of a dress
    public class Dress : ITop
    {
        public void Wear()
        {
            Console.WriteLine("Wearing a dress.");
        }
    }

     // A concrete product class that implements the abstract product interface and defines the specific behavior of trousers
     public class Trousers : IPants
     {
         public void Wear()
         {
             Console.WriteLine("Wearing trousers.");
         }
     }

     // A concrete product class that implements the abstract product interface and defines the specific behavior of jeans
     public class Jeans : IPants
     {
         public void Wear()
         {
             Console.WriteLine("Wearing jeans.");
         }
     }

     // A concrete product class that implements the abstract product interface and defines the specific behavior of a skirt
     public class Skirt : IPants
     {
         public void Wear()
         {
             Console.WriteLine("Wearing a skirt.");
         }
     }

     // A concrete product class that implements the abstract product interface and defines the specific behavior of formal shoes
     public class FormalShoes : IShoes
     {
         public void Wear()
         {
             Console.WriteLine("Wearing formal shoes.");
         }
     }

     // A concrete product class that implements the abstract product interface and defines the specific behavior of sneakers
     public class Sneakers : IShoes
     {
         public void Wear()
         {
             Console.WriteLine("Wearing sneakers.");
         }
     }

     // A concrete product class that implements the abstract product interface and defines the specific behavior of heels
     public class Heels : IShoes
     {
         public void Wear()
         {
             Console.WriteLine("Wearing heels.");
         }
     }

    // The driver class that uses the abstract factory interface to create and use products of different families
    public class GarmentSimulator
    {
        private ITop _top;
        private IPants _pants;
        private IShoes _shoes;

        // The constructor that accepts an abstract factory object and uses it to create products of a specific family
        public GarmentSimulator(IGarmentFactory factory)
        {
            _top = factory.CreateTop();
            _pants = factory.CreatePants();
            _shoes = factory.CreateShoes();
        }

        // A method that simulates wearing the products created by the factory
        public void WearGarments()
        {
            _top.Wear();
            _pants.Wear();
            _shoes.Wear();
        }
    }

    // The main program that tests the Abstract Factory pattern by creating different garment factories and simulators
    class Program
    {
        static void Main(string[] args)
        {
            // Create a professional garment factory and simulator
            IGarmentFactory professionalFactory = new ProfessionalGarmentFactory();
            GarmentSimulator professionalSimulator = new GarmentSimulator(professionalFactory);

            // Create a casual garment factory and simulator
            IGarmentFactory casualFactory = new CasualGarmentFactory();
            GarmentSimulator casualSimulator = new GarmentSimulator(casualFactory);

            // Create a party garment factory and simulator
            IGarmentFactory partyFactory = new PartyGarmentFactory();
            GarmentSimulator partySimulator = new GarmentSimulator(partyFactory);

            // Test the professional simulator
            Console.WriteLine("Testing the professional simulator:");
            professionalSimulator.WearGarments();

            // Test the casual simulator
            Console.WriteLine("\nTesting the casual simulator:");
            casualSimulator.WearGarments();

            // Test the party simulator
            Console.WriteLine("\nTesting the party simulator:");
            partySimulator.WearGarments();

            // Output:
            // Testing the professional simulator:
            // Wearing a shirt.
            // Wearing trousers.
            // Wearing formal shoes.

            // Testing the casual simulator:
            // Wearing a t-shirt.
            // Wearing jeans.
            // Wearing sneakers.

            // Testing the party simulator:
            // Wearing a dress.
            // Wearing a skirt.
            // Wearing heels.
        }
    }
}
