from datetime import datetime
import json

clients_db = []

def add_client(name, **kwargs):
    client_doc = {
        "_id": len(clients_db) + 1,
        "name": name.strip(),
        "created_at": datetime.now().isoformat(),
        **kwargs
    }
    clients_db.append(client_doc)
    return client_doc

add_client("Анна", sketch_url="anna_flower.jpg")
add_client("Дмитрий", appointment="2026-02-15", master="Иван")
add_client("Мария", allergies=["latex", "red_ink"], emergency_contact="+79991234567")

print(json.dumps(clients_db, indent=2, ensure_ascii=False))
