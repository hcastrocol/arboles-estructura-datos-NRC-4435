// Clase Nodo
class Nodo {
    int valor;
    Nodo izquierdo;
    Nodo derecho;
    
    public Nodo(int valor) {
        this.valor = valor;
        this.izquierdo = null;
        this.derecho = null;
    }
}

// Clase ArbolBinario
class ArbolBinario {
    private Nodo raiz;
    
    public ArbolBinario() {
        this.raiz = null;
    }
    
    // Método para insertar un valor en el árbol
    public void insertar(int valor) {
        raiz = insertarRecursivo(raiz, valor);
    }
    
    private Nodo insertarRecursivo(Nodo nodo, int valor) {
        // Si el árbol está vacío, retorna un nuevo nodo
        if (nodo == null) {
            return new Nodo(valor);
        }
        
        // En caso contrario, recorre el árbol
        if (valor < nodo.valor) {
            nodo.izquierdo = insertarRecursivo(nodo.izquierdo, valor);
        } else if (valor > nodo.valor) {
            nodo.derecho = insertarRecursivo(nodo.derecho, valor);
        }
        
        // Retorna el nodo sin cambios (evita duplicados)
        return nodo;
    }
    
    // Método para eliminar un valor del árbol
    public void eliminar(int valor) {
        raiz = eliminarRecursivo(raiz, valor);
    }
    
    private Nodo eliminarRecursivo(Nodo nodo, int valor) {
        // Caso base: árbol vacío
        if (nodo == null) {
            return null;
        }
        
        // Buscar el nodo a eliminar
        if (valor < nodo.valor) {
            nodo.izquierdo = eliminarRecursivo(nodo.izquierdo, valor);
        } else if (valor > nodo.valor) {
            nodo.derecho = eliminarRecursivo(nodo.derecho, valor);
        } else {
            // Nodo con un solo hijo o sin hijos
            if (nodo.izquierdo == null) {
                return nodo.derecho;
            } else if (nodo.derecho == null) {
                return nodo.izquierdo;
            }
            
            // Nodo con dos hijos: obtener sucesor inorder (mínimo en subárbol derecho)
            nodo.valor = valorMinimo(nodo.derecho);
            
            // Eliminar el sucesor inorder
            nodo.derecho = eliminarRecursivo(nodo.derecho, nodo.valor);
        }
        
        return nodo;
    }
    
    private int valorMinimo(Nodo nodo) {
        int valorMin = nodo.valor;
        while (nodo.izquierdo != null) {
            valorMin = nodo.izquierdo.valor;
            nodo = nodo.izquierdo;
        }
        return valorMin;
    }
    
    // Recorrido Inorder
    public void inorder() {
        inorderRecursivo(raiz);
        System.out.println();
    }
    
    private void inorderRecursivo(Nodo nodo) {
        if (nodo != null) {
            inorderRecursivo(nodo.izquierdo);
            System.out.print(nodo.valor + " ");
            inorderRecursivo(nodo.derecho);
        }
    }
    
    // Recorrido Preorder
    public void preorder() {
        preorderRecursivo(raiz);
        System.out.println();
    }
    
    private void preorderRecursivo(Nodo nodo) {
        if (nodo != null) {
            System.out.print(nodo.valor + " ");
            preorderRecursivo(nodo.izquierdo);
            preorderRecursivo(nodo.derecho);
        }
    }
    
    // Recorrido Postorder
    public void postorder() {
        postorderRecursivo(raiz);
        System.out.println();
    }
    
    private void postorderRecursivo(Nodo nodo) {
        if (nodo != null) {
            postorderRecursivo(nodo.izquierdo);
            postorderRecursivo(nodo.derecho);
            System.out.print(nodo.valor + " ");
        }
    }
}

// Clase principal
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        ArbolBinario arbol = new ArbolBinario();
        Scanner scanner = new Scanner(System.in);
        int opcion, valor;
        
        do {
            System.out.println("\n--- ÁRBOL BINARIO DE BÚSQUEDA ---");
            System.out.println("1. Insertar elemento");
            System.out.println("2. Eliminar elemento");
            System.out.println("3. Recorrido Inorder");
            System.out.println("4. Recorrido Preorder");
            System.out.println("5. Recorrido Postorder");
            System.out.println("0. Salir");
            System.out.print("Seleccione una opción: ");
            opcion = scanner.nextInt();
            
            switch (opcion) {
                case 1:
                    System.out.print("Ingrese valor a insertar: ");
                    valor = scanner.nextInt();
                    arbol.insertar(valor);
                    break;
                case 2:
                    System.out.print("Ingrese valor a eliminar: ");
                    valor = scanner.nextInt();
                    arbol.eliminar(valor);
                    break;
                case 3:
                    System.out.println("Recorrido Inorder:");
                    arbol.inorder();
                    break;
                case 4:
                    System.out.println("Recorrido Preorder:");
                    arbol.preorder();
                    break;
                case 5:
                    System.out.println("Recorrido Postorder:");
                    arbol.postorder();
                    break;
                case 0:
                    System.out.println("Saliendo del programa...");
                    break;
                default:
                    System.out.println("Opción inválida");
            }
        } while (opcion != 0);
        
        scanner.close();
    }
}
