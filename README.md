class Client:
    def __init__(self, name):
        self.name = name

    def make_order(self, waiter, order):
        waiter.take_order(self, order)

class Waiter:
    def __init__(self, name):
        self.name = name
        self.orders = []

    def take_order(self, client, order):
        self.orders.append((client.name, order))
        print(f"{self.name} received an order from {client.name} for {order}")

    def show_orders(self):
        print(f"Orders taken by {self.name}:")
        for client_name, order in self.orders:
            print(f"{client_name} ordered {order}")

client = Client("Nick")
waiter = Waiter("Kate")
client.make_order(waiter, "Americano")
client.make_order(waiter, "piece of Waffle cake")
waiter.show_orders()
