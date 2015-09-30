#include <iostream>
using namespace std;
 
int main()
{
    // Puntero a una matriz
    int **pm;
 
    int cols;
    int rows;
 
    cout << "Ingresa nro de filas: ";
    cin >> rows;
 
    cout << endl;
    cout << "Ingresa nro de columnas: ";
    cin >> cols;
 
    pm = new int* [rows];
    for (int i = 0; i < rows; i++) {
        pm[i] = new int[cols]; //Asignando  una matriz pm[rows][cols]
    }
    
    
 	cout << "\nMatriz" <<endl;
 	for(int i = 0; i < rows; i++)
 	{
 		cout<<"\t\t";
 		for(int j = 0; j < cols; j++){
 			
			 /*pm[i][j] = i + j;
			 cout << pm[i][j] <<"\t";*/
			 cin>>pm[i][j];
			 
		 }
		 cout << "\n"<<endl;
	 }
    
	
	cout << "Elementos de la Matriz con sus direcciones: " << endl;
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            pm[i][j] = i + j;
            cout << pm[i][j] << "--> ";
            cout << &pm[i][j] << endl;
        }
        cout << endl;
    }
    cout << endl;
 
    cout << "Elementos de la Matriz con sus direcciones, con aritmética de punteros: " << endl;
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            // Aritmética de punteros
            *(*(pm + i) + j) = i + j;
            cout << *(*(pm + i) + j) << "--> ";
            cout << &pm[i][j] << endl;
        }
        cout << endl;
    }
 
    // Elimino cada vector de la matriz
    for (int i = 0; i < rows; i++) {
        delete[] pm[i];
    }
 
    // Elimino el vector principal
    delete[] pm;
 
    return 0;
}
