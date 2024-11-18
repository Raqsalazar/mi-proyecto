# mi-proyecto
diferencias_sistemas_control.js
// Ejemplo básico de sistemas centralizados y distribuidos

// Sistema Centralizado
class CentralizedSystem {
  constructor() {
    this.data = { usuario1: "dato1", usuario2: "dato2" }; // Todos los datos en un servidor
  }

  getData(user) {
    return this.data[user] || "Usuario no encontrado";
  }
}

// Sistema Distribuido
class DistributedSystem {
  constructor() {
    // Los datos se distribuyen en varios nodos
    this.nodes = { nodo1: { usuario1: "dato1" }, nodo2: { usuario2: "dato2" } };
  }

  getData(user) {
    for (const node in this.nodes) {
      if (this.nodes[node][user]) return `${this.nodes[node][user]} (en ${node})`;
    }
    return "Usuario no encontrado";
  }
}

// Ejemplo de uso
const central = new CentralizedSystem();
console.log("Centralizado:", central.getData("usuario1")); // dato1

const distributed = new DistributedSystem();
console.log("Distribuido:", distributed.getData("usuario2")); // dato2 (en nodo2)
