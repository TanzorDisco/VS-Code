Console Progress Bar Example

```
class Program
	{
		const char _block = '■';
		const string _back = "\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b";

		static async Task Main(string[] args)
		{
			Console.Write("Something is out: ");

			WriteProgressBar(0);

			for (var i = 0; i <= 100; ++i)
			{
				WriteProgressBar(i, true);
				Thread.Sleep(50);
			}

			Console.WriteLine();

			await Task.CompletedTask;
		}


		public static void WriteProgressBar(int percent, bool update = false)
		{
			if (update)
				Console.Write(_back);
			Console.Write("[");
			var p = (int)((percent / 10f) + .5f);
			for (var i = 0; i < 10; ++i)
			{
				if (i >= p)
					Console.Write(' ');
				else
					Console.Write(_block);
			}
			Console.Write("] {0,3:##0}%", percent);
		}
	}
```
