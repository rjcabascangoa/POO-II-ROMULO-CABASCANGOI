class Node:
    """ representa un nodo en una lista enlazada."""
    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:
    """Clase que representa una lista enlazada."""
    def __init__(self):
        self.head = None

    def append(self, data):
        """Agrega un nuevo nodo al final de  lista."""
        new_node = Node(data)
        if not self.head:
            self.head = new_node
            return
        current = self.head
        while current.next:
            current = current.next
        current.next = new_node

    def display(self):
        """Muestra los elementos de la lista."""
        elements = []
        current = self.head
        while current:
            elements.append(current.data)
            current = current.next
        print(" -> ".join(map(str, elements)))

    def reverse(self):
        """Invierte los elementos  lista enlazada."""
        prev = None
        current = self.head
        while current:
            next_node = current.next  # Guarda el siguiente nodo
            current.next = prev       # Invierte la dirección del enlace
            prev = current            # Avanza el puntero prev
            current = next_node       # Avanza al siguiente nodo
        self.head = prev  # Actualiza la cabeza de la lista

###################################################################
Ejercicio 2
Crear una lista enlazada con 50 números enteros, del 1 al 999 generados aleatoriamente. Una
vez creada la lista, vez creada la lista, se deben eliminar los nodos qu se deben eliminar los nodos que estén fuera de un r e estén fuera de un rango de valores leídos ango de valores leídos
desde el teclado

###################################################################
import random

class Node:
    """Clase que representa un nodo en una lista enlazada."""
    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:
    """Clase que representa una lista enlazada."""
    def __init__(self):
        self.head = None

    def append(self, data):
        """Agrega un nuevo nodo al final de la lista."""
        new_node = Node(data)
        if not self.head:
            self.head = new_node
            return
        current = self.head
        while current.next:
            current = current.next
        current.next = new_node

    def display(self):
        """Muestra los elementos de la lista."""
        elements = []
        current = self.head
        while current:
            elements.append(current.data)
            current = current.next
        print(" -> ".join(map(str, elements)))

    def remove_out_of_range(self, low, high):
        """Elimina los nodos que estén fuera del rango especificado."""
        # Manejar el caso especial del primer nodo
        while self.head and (self.head.data < low or self.head.data > high):
            self.head = self.head.next

        current = self.head
        while current and current.next:
            if current.next.data < low or current.next.data > high:
                current.next = current.next.next  # Salta el nodo fuera del rango
            else:
                current = current.next

# Generar la lista enlazada con números aleatorios
linked_list = LinkedList()
for _ in range(50):
    linked_list.append(random.randint(1, 999))

print("Lista original:")
linked_list.display()

# Leer el rango de valores desde el teclado
low = int(input("Ingrese el límite inferior del rango: "))
high = int(input("Ingrese el límite superior del rango: "))

# Eliminar nodos fuera del rango
linked_list.remove_out_of_range(low, high)

print("\nLista después de eliminar nodos fuera del rango:")
linked_list.display()

