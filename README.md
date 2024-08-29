## Idea
Original [donut.c](https://www.a1k0n.net/2011/07/20/donut-math.html) idea from Andy Sloane's blog.


## Code
```csharp
static void Main(string[] args)
        { 
            Console.SetWindowSize(100, 40); 
            double A = 0, B = 0;
            double i, j;
            var z = new double[7040];
            var b = new char[1760];
            while (true)
            {
                memset(b, ' ', 1760);
                memset(z, 0.0, 7040);
                for (j = 0; j < 6.28; j += 0.07)
                {
                    for (i = 0; i < 6.28; i += 0.02)
                    {
                        double c = Math.Sin(i);
                        double d = Math.Cos(j);
                        double e = Math.Sin(A);
                        double f = Math.Sin(j);
                        double g = Math.Cos(A);
                        double h = d + 2;
                        double D = 1 / (c * h * e + f * g + 5);
                        double l = Math.Cos(i);
                        double m = Math.Cos(B);
                        double n = Math.Sin(B);
                        double t = c * h * g - f * e;

                        int x = (int)(40 + 30 * D * (l * h * m - t * n));
                        int y = (int)(12 + 15 * D * (l * h * n + t * m));
                        int o = x + 80 * y;
                        int N = (int)(8 * ((f * e - c * d * g) * m - c * d * e - f * g - l * d * n));

                        if (y > 0 && y < 22 && x > 0 && x < 80 && D > z[o])
                        {
                            z[o] = D;
                            b[o] = ".,-~:;=!*#$@"[N > 0 ? N : 0];
                        }
                    }
                }
                Console.Clear();
                Console.Write(b);
                A += 0.04;
                B += 0.02;
                Thread.Sleep(50);
            }
        }

        static void memset<T>(T[] buf, T val, int bufsz)
        {
            if (buf == null) buf = new T[bufsz];
            for (int i = 0; i < bufsz; i++) buf[i] = val;
        }

```
