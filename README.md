# Word-Couting
软件技术基础作业01
      
#include<fstream>
#include<iostream>
#include <cassert>

using namespace std;
int character = 0, words = 0, sentence = 0, line = 1, emptyLine = 0;
char temp[1024] = { 0 };
int i=0;
void readTxt(string file)
{
    ifstream infile;
    infile.open(file.data());
    assert(infile.is_open());

    char c;
    infile >> noskipws;
    while (infile.peek() != EOF)
    {
        infile >> temp[i];
        cout << temp[i];
        if (temp[i] == temp[i - 1] && temp[i] == '\n') { emptyLine++; }
        switch (temp[i])
        {
        case ' ':words++; break;
        case '.':words; sentence++; break;
        case '？':sentence++; break;
        case '！':sentence++; break;
        case '\n':line++; break;
        default:character++; break;
        }
        i++;
    }
    infile.close();
}

int main()
{
    readTxt("Test.txt");
    cout << endl << endl;
    cout << "字符:" << character << endl;
    cout << "单词:" << words << endl;
    cout << "句子: " << sentence << endl;
    cout << "行数: " << line << endl;
    cout << "空行: " << emptyLine << endl;
    system("PAUSE");
    return 0;

}
      
      
