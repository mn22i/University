/* inheritance-inC#-
Super class named Point containing:
	An instance variable named x of type int.
	An instance variable named y of type int.
	Write a Sub class named Circle containing: Constructor that accepts values of all data members as arguments.
	Get and Set methods for data fields.
	Declare a method named ToString() Returns a string representation of the point*/

 public class Point
        {
            private int X;
            private int Y;

            public Point()
            {
                this.X = 1;
                this.Y = 2;

            }
            public Point(int x, int y)
            {
                this.X= x;
                this.Y = y;

            }
            public int getsetX
            {
                get
                {
                    return X;

                }
                set
                {
                    X = value;
                }


               
            }
            public int getsetY
            {
                get
                {
                    return Y;

                }
                set
                {
                    Y= value;
         
         }



            }
            public string ToString()
            {
                return "X = " + X + "Y =" + Y;
            }



        } 
      /*  •	Write a Sub class named Circle containing:
	Circle(x, y, radius)
Constructs a new circle with a radius (double) and inherit the (x, y) coordinates of its center from its super class Point.
-	GetRadius()
Returns the value of radius.
.	SetRadius
Sets the value of radius.
-	GetArea()
Returns the area occupied by the circle, using the formula πr2.
-	GetCircumference()
Returns the circle's circumference (distance around the circle), using the
formula 2πr.
-	ToString()
Returns a string representation of the circle, such as "Circle [center=(75, 20); radius=30]".
*/
 class Circle : Point
        {
            private double radius;
            public Circle(double r , int x, int y ) : base() { this.radius = r;
               
            }


            public double getsetRaduis
            {
                get { return radius; }
                set { radius = value; }
            }
            public double GetArea()
            {
                return radius * radius * Math.PI;
            }
             public double GetCircumference()
            {
                return Math.PI * 2 * radius;
            }
            public   string ToString()
            {
                return "Circle [center=(" + getsetX + "," + getsetY + "); Radius ="+getsetRaduis+ "]" ;
            }


        }
        //Main
        static void Main(string[] args)
        {


            Point c= new Point();
            c.ToString();

            Circle s = new Circle(22,75,24);
            Console.WriteLine(s.ToString());
               
            s.GetArea();
            Console.WriteLine("Area is :{0}  ",s.GetArea());
            s.GetCircumference();
            Console.WriteLine("Circumference is : {0}",s.GetCircumference());
           // s.ToString();
         
            
            Console.ReadKey();


        }
