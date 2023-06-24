#define RESET   "\033[0m"
#define RED     "\033[31m"
#define GREEN   "\033[32m"
#define YELLOW  "\033[33m"
#define BLUE    "\033[34m"
#define MAGENTA "\033[35m"
#define CYAN    "\033[36m"
#define WHITE   "\033[37m"
#include <iostream>
using namespace std;
char nguoichoi = 'X';
int soDong, soCot;
char banco[100][100];
void vebanco()
{
    for (int i = 0; i < soDong; i++)
    {
        cout << "\t\t\t\t\t\t\t";
        for (int j = 0; j < soCot; j++)
        {
            cout << string(RED)+" ___ "+RESET;
        }
        cout << endl;
        cout << "\t\t\t\t\t\t\t";
        for (int j = 0; j < soCot; j++)
        {
            cout << string(CYAN)+"|" << "_" << banco[i][j] << "_"<< "|"<<RESET;
        }
        cout << endl;
    }
}
void NhapXO()
{
    int n;
    cout << "Nhap vao vi tri can danh: ";
    cin >> n;
    int x = (n - 1) / soCot;
    int y = (n - 1) % soCot;
    if (banco[x][y] == '_')
    {
        banco[x][y] = nguoichoi;
        nguoichoi = (nguoichoi == 'X') ? 'O' : 'X';
    }
    else
    {
        cout << "Vi tri da duoc danh, vui long nhap lai." << endl;
        NhapXO();
    }
}
bool kiemtra(char a, char b, char c, char d, char e){
    return (a == b && b == c && c == d && d == e && a!='_');  // 1 
}
char nguoichienthang() // 2 
{
    for (int i = 0; i < soDong; i++)
    {
        for (int j = 0; j < soCot; j++)
        {
            if (j + 4 < soCot && kiemtra(banco[i][j], banco[i][j + 1], banco[i][j + 2], banco[i][j + 3], banco[i][j + 4]))
                return banco[i][j];
            if (i + 4 < soDong && kiemtra(banco[i][j], banco[i + 1][j], banco[i + 2][j], banco[i + 3][j], banco[i + 4][j]))
                return banco[i][j];
            if (i + 4 < soDong && j + 4 < soCot && kiemtra(banco[i][j], banco[i + 1][j + 1], banco[i + 2][j + 2], banco[i + 3][j + 3], banco[i + 4][j + 4]))
                return banco[i][j];
            if (i >= 4 && j + 4 < soCot && kiemtra(banco[i][j], banco[i - 1][j + 1], banco[i - 2][j + 2], banco[i - 3][j + 3], banco[i - 4][j + 4]))
                return banco[i][j];
        }
    }
    return '_';
}
void tennguoithunhat(){
    string name1;  cin.ignore();
    cout <<"Nhap vao ten nguoi choi thu nhat: ";
    getline(cin,name1);
    cout <<"Ten nguoi choi thu nhat la: "<<name1<<endl;
}
void tennguoithuhai(){
    string name2;  cin.ignore();
    cout <<"Nhap vao ten nguoi choi thu hai: ";
    getline(cin,name2);
    cout <<"Ten nguoi choi thu hai la: "<<name2<<endl;
}
int main()
{
    cout << "\t\t\t\t" + string(RED) + "+-------------------------------------------------------------------------------------------------+" + RESET << endl;
    cout << "\t\t\t\t" + string(RED) + "|     #####       #       #######         # # # #          # # # #     #           #    # # # #   |" + RESET << endl;
    cout << "\t\t\t\t" + string(RED) + "|   #            # #      #      #      #         #        #             #       #      #         |" + RESET << endl;
    cout << "\t\t\t\t" + string(RED) + "|  #            #   #     #       #    #           #       #               #   #        #         |" + RESET << endl;
    cout << "\t\t\t\t" + string(RED) + "|  #           #######    ########    #             #      # # # #           #          # # # #   |" + RESET << endl;
    cout << "\t\t\t\t" + string(RED) + "|  #          #       #   #       #    #           #               #       #   #                # |" + RESET << endl;
    cout << "\t\t\t\t" + string(RED) + "|   #        #         #  #        #    #         #                #     #       #              # |" + RESET << endl;
    cout << "\t\t\t\t" + string(RED) + "|     ##### #           # #         #     # # # #          # # # #     #           #    # # # #   |" + RESET << endl;
    cout << "\t\t\t\t" + string(RED) + "+-------------------------------------------------------------------------------------------------+" + RESET << endl;
    cout << "\t\t\t\t\t\t\t\t" + string(YELLOW) + "+---------------------------+"+RESET<<endl;
    cout << "\t\t\t\t\t\t\t\t" + string(GREEN)  + "| 1 Ten nguoi choi thu nhat |"+RESET<<endl;
    cout << "\t\t\t\t\t\t\t\t" + string(YELLOW) + "+---------------------------+"+RESET<<endl;
    cout << "\t\t\t\t\t\t\t\t" + string(BLUE)   + "| 2 Ten nguoi choi thu hai  |"+RESET<<endl;
    cout << "\t\t\t\t\t\t\t\t" + string(YELLOW) + "+---------------------------+"+RESET<<endl;
    cout << "\t\t\t\t\t\t\t\t" + string(MAGENTA)+ "| 3 Bat dau choi            |"+RESET<<endl;
    cout << "\t\t\t\t\t\t\t\t" + string(YELLOW) + "+---------------------------+"+RESET<<endl;
    cout << "\t\t\t\t\t\t\t\t" + string(CYAN)   + "| 4 Thoat                   |"+RESET<<endl;
    cout << "\t\t\t\t\t\t\t\t" + string(YELLOW) + "+---------------------------+"+RESET<<endl;
    int lc;
    do
    {
        cout << "Nhap lua chon cua ban: ";
        cin >> lc;
        if (lc == 1)
        {
            tennguoithunhat();
        }
        else if (lc == 2)
        {
            tennguoithuhai();
        }
        else if (lc == 3)
        {
            cout << "Nhap vao so dong cua ban co: ";
            cin >> soDong;
            cout << "Nhap vao so cot cua ban co: ";
            cin >> soCot;
            for (int i = 0; i < soDong; i++)
            {
                for (int j = 0; j < soCot; j++)
                {
                    banco[i][j] = '_';
                }
            }
            vebanco();
            for (int i = 0; i < soDong * soCot; i++)  // 3
            {
                NhapXO();
                system("cls");
                vebanco();
                char chien_thang = nguoichienthang();
                if (chien_thang == 'X')
                {
                    cout << "X chien thang" << endl;
                    break;
                }
                else if (chien_thang == 'O')
                {
                    cout << "O chien thang" << endl;
                    break;
                }
            }
        }
    }while(lc!=4);
}
