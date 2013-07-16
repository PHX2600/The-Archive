## final class project
Posted by **TerrorDrone** on Wed November 18th, 2009 11:07:37 AM

here is my final project for my c class it isnt exactley where i want it to be but got an A 
it determines the value of a resistor along with the upper and lower variance
[code:1ljv3iet]//*Casey Dekker
//ET156
//Resistor Color Code

#include &lt;stdio&#46;h&gt;
#include &lt;stdlib&#46;h&gt;
#include &lt;conio&#46;h&gt;

void doFourBand(void);
void doFiveBand(void);
double getMultiplyer(int);
void printKey(void);
char resistorColor&#91;&#93;&#91;10&#93; = {&quot;Black&quot;, &quot;Brown&quot;, &quot;Red&quot;, &quot;Orange&quot;, &quot;Yellow&quot;, &quot;Green&quot;, &quot;Blue&quot;, &quot;Voilet&quot;, &quot;Gray&quot;, &quot;White&quot;};
double getTolerance(void);
void getFiveBandTolerance(int);

int main(void)
{
	int selection;
	do 
	{
		// Create menu for user to select which type of resistor to calculate
		printf(&quot;Select resistor type&#58;\n&quot;);
		printf(&quot;1) 4 Band\n&quot;);
		printf(&quot;2) 5 Band\n&quot;);
		printf(&quot;3) Exit\n&quot;);
		printf(&quot;Enter Selection&#58; &quot;);
	
		scanf(&quot;%i&quot;, &amp;selection);

		if(selection == 1)
			doFourBand();
		if(selection == 2)
			doFiveBand();

	} while (selection != 3);
	return 0;
}

void doFourBand(void) {
	
	int bandColor&#91;4&#93;;
	system(&quot;cls&quot;);
	printKey();
	printf(&quot;Four Band Resistor\n&quot;);
	
	printf(&quot;USE FOLLOWING LEGEND&#58;\n&quot;);
	printf(&quot; COLOR		NUMBER\n&quot;);
	printf(&quot;BLACK			(0)\n&quot;);
	printf(&quot;BROWN			(1)\n&quot;);
	printf(&quot;RED			(2)\n&quot;);
	printf(&quot;ORANGE			(3)\n&quot;);
	printf(&quot;YELLOW			(4)\n&quot;);
	printf(&quot;GREEN			(5)\n&quot;);
	printf(&quot;BLUE			(6)\n&quot;);
	printf(&quot;VIOLET			(7)\n&quot;);
	printf(&quot;GRAY			(8)\n&quot;);
	printf(&quot;WHITE			(9)\n\n&quot;);
	
	for(int x = 1; x &lt;= 3;x++)
	{
		printf(&quot;Enter Band #%i&#58; &quot;, x);
		scanf(&quot;%i&quot;, &amp;bandColor&#91;x - 1&#93;);
	}
	
	int resistorValue = bandColor&#91;0&#93; * 10;
	resistorValue += bandColor&#91;1&#93;;
	resistorValue *= getMultiplyer(bandColor&#91;2&#93;);
	
	double tolerance = getTolerance();
	
	double high = (double)resistorValue + ((double)resistorValue * tolerance);
	double low = (double)resistorValue - ((double)resistorValue * tolerance);
	printf(&quot;\nResistor Value&#58; %i ohms&quot;, resistorValue);
	printf(&quot;\nHigh Variance&#58; %&#46;0f ohms&quot;, high);
	printf(&quot;\nLow Variance&#58; %&#46;0f ohms\n\n&quot;, low);
}

void doFiveBand(void)
{
	int bandColor&#91;5&#93;;
	system(&quot;cls&quot;);
	printKey();
	printf(&quot;Four Band Resistor\n&quot;);
	
		printf(&quot;USE THE FOLLOWING LEGEND&#58;\n&quot;);
		printf(&quot; COLOR		NUMBER\n&quot;);
		printf(&quot;BLACK			(0)\n&quot;);
		printf(&quot;BROWN			(1)\n&quot;);
		printf(&quot;RED			(2)\n&quot;);
		printf(&quot;ORANGE			(3)\n&quot;);
		printf(&quot;YELLOW			(4)\n&quot;);
		printf(&quot;GREEN			(5)\n&quot;);
		printf(&quot;BLUE			(6)\n&quot;);
		printf(&quot;VIOLET			(7)\n&quot;);
		printf(&quot;GRAY			(8)\n&quot;);
		printf(&quot;WHITE			(9)\n&quot;);
		printf(&quot;SILVER			(10)\n&quot;);
		printf(&quot;GOLD			(11)\n\n&quot;);
	for(int x = 1; x &lt;= 5;x++)
	{

		printf(&quot;Enter Band #%i&#58; &quot;, x);
		scanf(&quot;%i&quot;, &amp;bandColor&#91;x - 1&#93;);
	}
	
	double resistorValue = bandColor&#91;0&#93; * 100;
	resistorValue += bandColor&#91;1&#93; * 10;
	resistorValue += bandColor&#91;2&#93;;
	resistorValue *= getMultiplyer(bandColor&#91;3&#93;);


	//printf(&quot;%&#46;2f\n&quot;, resistorValue);

	//resistorValue *= getMultiplyer(bandColor&#91;2&#93;);
	
	//double tolerance = getTolerance();
	
	//double high = (double)resistorValue + ((double)resistorValue * tolerance);
	//double low = (double)resistorValue - ((double)resistorValue * tolerance);
	printf(&quot;\nResistor Value&#58; %&#46;2f ohms &quot;, resistorValue);
	getFiveBandTolerance(bandColor&#91;4&#93;);
	printf(&quot;\n\n&quot;);
	//printf(&quot;\nHigh Variance&#58; %&#46;0f ohms&quot;, high);
	//printf(&quot;\nLow Variance&#58; %&#46;0f ohms\n\n&quot;, low);
}

void getFiveBandTolerance(int t)
{
	switch (t)
	{
		case 0&#58;
			printf(&quot;+/-20%%&quot;);
			break;
		case 1&#58;
			printf(&quot;+/-1%%&quot;);
			break;
		case 2&#58;
			printf(&quot;+/-2%%&quot;);
			break;
		case 3&#58; 
			printf(&quot;+/-3%%&quot;);
			break;
		case 4&#58;
			printf(&quot;-0, +100%%&quot;);
			break;
		case 5&#58;
			printf(&quot;+/-0&#46;05%%&quot;);
			break;
		case 6&#58;
			printf(&quot;+/- 0&#46;25%%&quot;);
			break;
		case 7&#58;
			printf(&quot;+/-0&#46;10%%&quot;);
			break;
		case 8&#58; 
			printf(&quot;+/-0&#46;05%%&quot;);
			break;
		case 9&#58;
			printf(&quot;+/- 10%%&quot;);
			break;
		case 10&#58;
			printf(&quot;+/-10%%&quot;);
			break;
		case 11&#58;
			printf(&quot;+/-5%%&quot;);
			break;
		case 12&#58;
			printf(&quot;+/-20%%&quot;);
			break;


	}

}

double getMultiplyer(int m)
{
	switch (m)
	{
		case 0&#58;
			return 1;
			break;
		case 1&#58;
			return 10;
			break;
		case 2&#58;
			return 100;
			break;
		case 3&#58;
			return 1000;
			break;
		case 4&#58;
			return 10000;
			break;
		case 5&#58;
			return 100000;
			break;
		case 6&#58;
			return 1000000;
			break;
		case 7&#58;
			return 10000000;
			break;
		case 8&#58;
			return 100000000;
			break;
		case 9&#58;
			return 1000000000;
			break;
		case 10&#58;
			return 0&#46;01;
			break;
		case 11&#58;
			return 0&#46;1;
			break;

	}

	return 0;
}

void printKey(void)
{
	for(int x = 0; x &lt;=10; x++)
	{
		//printf(&quot;%6s = %i&quot;, resistorColor&#91;&#93;&#91;x&#93;, x);
	}
}

double getTolerance(void)
{
	int tolerance;
	do
	{
		printf(&quot;1) Gold (5%%)\n&quot;);
		printf(&quot;2) Silver (10%%)\n&quot;);
		printf(&quot;3) None (20%%)\n&quot;);
		printf(&quot;Enter Selection&#58; &quot;);
		scanf(&quot;%i&quot;, &amp;tolerance);
		if(tolerance &lt; 1 || tolerance &gt; 3)
		{
			printf(&quot;Invalid Selection\n\n&quot;);
		}
	} while (tolerance &lt; 1 || tolerance &gt; 3);

	if(tolerance == 1)
		return &#46;05;
	else if(tolerance == 2)
		return &#46;1;
	else
		return &#46;2;
}
[/code:1ljv3iet]
