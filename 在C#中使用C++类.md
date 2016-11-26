# Use C++ Class in C# #
## 编写C++程序 ##
项目名称：CppComputing</br>
header.h
<pre><code>#pragma once
#include &lt vector>

using namespace std;
class computingClass{
public:
	computingClass(int* pInt, int arrSize);
	int sumArray();
private:
	vector<int> vec;
};
</code></pre>
body.cpp
<pre><code>#pragma once
#include"header.h"

computingClass::computingClass(int *pInt, int arrSize){
	for (int i = 0; i < arrSize; i++)
	{
		vec.push_back(pInt[i]);
	}
}

int computingClass::sumArray(){
	int cumSum = 0;
	for (int i = 0; i < vec.size(); i++){
		cumSum += vec[i];
	}
	return cumSum;
}
</code></pre>
main.cpp
<pre><code>#include "header.h"
void main(){
	int noElements = 3;
	int *myArray = new int[3];

	myArray[0] = 10;
	myArray[1] = 15;
	myArray[2] = 75;
	computingClass cC(myArray, noElements);
	double sum = cC.sumArray();
}
</code></pre>
## 编写CLR代码 ##
新建->Visual C++->CLR</br>
项目名称：CppWrapper</br>
CppWrapper.h
<pre><code>#pragma once
#include"E:\test\CppComputingC\CppComputingC\header.h"
#include "E:\test\CppComputingC\CppComputingC\body.cpp"
using namespace System;

namespace CppWrapper {

	public ref class CppWrapperClass
	{
	public:
		CppWrapperClass(int *pInt, int arraySize);
		int getSum();
		int sum;
	private:
		computingClass* pCC;
		// TODO:  在此处添加此类的方法。
	};
}
</code></pre>
CppWrapper.cpp
<pre><code>// 这是主 DLL 文件。
#include "stdafx.h"
#include "CppWrapper.h"

CppWrapper::CppWrapperClass::CppWrapperClass(int *pInt, int arraySize){
	pCC = new computingClass(pInt, arraySize);
}
int CppWrapper::CppWrapperClass::getSum(){
	sum = pCC->sumArray();
	return sum;
}
</code></pre>
编译生成.dll文件，这个dll文件可以供C#使用
## C#控制台应用程序 ##
新建C#控制台应用程序ConsoleApplication1</br>
项目->引用->添加引用->浏览找到CLR生成的.dll文件并包含进来,即可像是用C#类一样使用这个C++类</br>
Program.cs</br>
<pre><code>using System;
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
            int noElements = 1000;
            int[] myArray = new int[noElements];

            for (int i = 0; i < noElements; i++)
                myArray[i] = i * 10;
            unsafe
            {
                fixed (int* pmyArray = &myArray[0])
                {
                    CppWrapper.CppWrapperClass controlCpp = new CppWrapper.CppWrapperClass(pmyArray, noElements);
                    controlCpp.getSum();
                    int sumOfArray = controlCpp.sum;
                }
            }
        }
    }
}
</code></pre>
