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


