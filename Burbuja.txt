#include <iostream>
#include <locale.h>

using namespace std;

int main() {
	setlocale(LC_ALL, "");
	
	int tamano;
	cout << "Digita el tamaño del arreglo de números: "; cin >> tamano;
	
	if(tamano <= 0) {
		cout << endl << "El tamaño del arreglo debe ser de, al menos, 1";
		return 0;
	}
	
	int array[tamano];
	int estado = 'F';
	int min = 0, mitad, temp, dato, max = tamano;
	
	for(int i = 0; i < tamano; i++) {
		cout << "Digita el valor " << i+1 << " del arreglo: ";
		cin >> array[i];
	}
	
	//Impresión del array inicial
	cout << endl << "Arreglo inicial" << endl << "[ ";
	for(int i = 0; i < tamano; i++) {
		cout << array[i] << " ";
	}
	cout << "]" << endl << endl;
	
	// Algoritmo de ordenamiento (Burbuja)
	for(int i = 0; i < tamano; i++) {
		for(int j = 0; j < (tamano - i - 1); j++) {
			if (array[j] > array[j + 1]) {
				temp = array[j];
				array[j] = array[j + 1];
				array[j + 1] = temp;  
			} 
		}
	}
	
	//Impresión del array ordenado
	cout <<"Arreglo ordenado" << endl << "[ ";
	for(int i = 0; i < tamano; i++) {
		cout << array[i] << " ";
	}
	cout << "]" << endl;
	
	
	cout << endl << "Digita el dato que deseas encontrar en el array: "; cin >> dato;
	
	//Algoritmo de búsqueda Binaria
	while(min <= max) {
		mitad = (min + max)/2;
		
		if(array[mitad] == dato) {
			estado = 'V';
			break;
		}
		if(array[mitad] > dato) {
			max = mitad;
			mitad = (min + max)/2;
		}
		if(array[mitad] < dato) {
			min = mitad;
			mitad = (min + max)/2;
		}
	}
	
	if(estado == 'V') {
		cout << endl << "El número se encuentra en la posición: " << mitad;
	}
	
	return 0;
}