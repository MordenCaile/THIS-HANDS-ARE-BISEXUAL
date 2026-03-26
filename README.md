# THIS-HANDS-ARE-BISEXUAL
Progetto per CLIL di GPOI

progetto modificato e uploadato:
applicazione web/applicazione downloadabile che permette di
1. registrazione utente
2. geolocalizzazione
3. creazione squadre singole
4. crazione squadre in lega
5. creazione squadre in tornei
6. creazione eventi (leghe/tornei)
7. opzione di geolicalizzazione degli eventi e registrazione dei luoghi degli eventi
8. database con TUTTE LE SQUADRE UFFICIALI
9. database con TUTTE LE SQUADRE SECRET
10. funzionalità di base per tutti, massimo una lega, massimo un torneo alla volta
11. funzionalità premium, fino a 20 squadre, no limite eventi, possibilità di fare i playoff

CODICE REACT DA VERIFICARE
import React, { useState } from "react";
import { Home, Users, Trophy, Menu } from "lucide-react";

export default function App() {
  const [sidebarOpen, setSidebarOpen] = useState(false);
  const [page, setPage] = useState("home");

  const renderPage = () => {
    switch (page) {
      case "teams":
        return <h1 className="text-xl">Team Builder</h1>;
      case "leagues":
        return <h1 className="text-xl">League Manager</h1>;
      case "matches":
        return <h1 className="text-xl">Match Entry</h1>;
      default:
        return <h1 className="text-xl">Dashboard</h1>;
    }
  };

  return (
    <div className="flex h-screen bg-gray-100">
      {/* Sidebar */}
      <div
        className={`bg-gray-900 text-white w-64 p-5 fixed h-full transition-transform ${
          sidebarOpen ? "translate-x-0" : "-translate-x-full"
        }`}
      >
        <h2 className="text-2xl mb-6">Blood Bowl App</h2>
        <nav className="space-y-4">
          <button
            onClick={() => setPage("home")}
            className="flex items-center gap-2 hover:text-gray-300"
          >
            <Home size={20} /> Dashboard
          </button>
          <button
            onClick={() => setPage("teams")}
            className="flex items-center gap-2 hover:text-gray-300"
          >
            <Users size={20} /> Teams
          </button>
          <button
            onClick={() => setPage("leagues")}
            className="flex items-center gap-2 hover:text-gray-300"
          >
            <Trophy size={20} /> Leagues
          </button>
          <button
            onClick={() => setPage("matches")}
            className="flex items-center gap-2 hover:text-gray-300"
          >
            ⚔ Matches
          </button>
        </nav>
      </div>

      {/* Main Content */}
      <div className="flex-1 ml-0 md:ml-64 p-6">
        {/* Topbar */}
        <div className="flex items-center justify-between mb-6">
          <button
            onClick={() => setSidebarOpen(!sidebarOpen)}
            className="md:hidden"
          >
            <Menu />
          </button>
          <h1 className="text-2xl font-bold">Blood Bowl Manager</h1>
        </div>

        {/* Page Content */}
        <div className="bg-white p-6 rounded-2xl shadow">
          {renderPage()}
        </div>
      </div>
    </div>
  );
}
