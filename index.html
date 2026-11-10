<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Juicy Veggie Builder - An Việt Mộc</title>
  <!-- React & ReactDOM CDN -->
  <script src="https://unpkg.com/react@18/umd/react.production.min.js" crossorigin></script>
  <script src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js" crossorigin></script>
  <!-- Babel Standalone for JSX -->
  <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
  <!-- Tailwind CSS CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;600;700;800&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'Plus Jakarta Sans', sans-serif;
      background: linear-gradient(135deg, #fff5f8 0%, #f0f7ff 50%, #f5fff8 100%);
      min-height: 100vh;
    }
    .skittle-card {
      transition: all 0.25s cubic-bezier(0.34, 1.56, 0.64, 1);
    }
    .skittle-card:hover {
      transform: translateY(-4px) scale(1.02);
    }
    .skittle-card:active {
      transform: scale(0.97);
    }
    .glass-nav {
      background: rgba(255, 255, 255, 0.85);
      backdrop-filter: blur(12px);
    }
    .rainbow-border {
      position: relative;
    }
    .rainbow-border::after {
      content: '';
      position: absolute;
      inset: -2px;
      border-radius: 1.25rem;
      background: linear-gradient(45deg, #ff4e50, #f9d423, #00e676, #00b0ff, #d500f9);
      z-index: -1;
      opacity: 0;
      transition: opacity 0.3s ease;
    }
    .rainbow-border.selected::after {
      opacity: 1;
    }
  </style>
</head>
<body class="pb-32">
  <div id="root"></div>

  <script type="text/babel">
    const { useState, useEffect, useMemo } = React;

    // Direct Google Sheet ID
    const SPREADSHEET_ID = '1m02-1ymsbJiTDo29hVtsbrV85cm3E0MF2UB2HgbFYl4';
    const OPEN_SHEET_URL = `https://opensheet.elk.sh/${SPREADSHEET_ID}/1`;

    const CATEGORY_MAP = {
      "Leafy Greens": { nameEn: "Leafy Greens", nameVn: "Nhóm Rau", icon: "🥬", color: "bg-emerald-500", light: "bg-emerald-50 text-emerald-700" },
      "Fruiting Vegetables & Gourds": { nameEn: "Fruiting Veggies", nameVn: "Nhóm Quả", icon: "🫑", color: "bg-rose-500", light: "bg-rose-50 text-rose-700" },
      "Roots & Tubers": { nameEn: "Roots & Tubers", nameVn: "Nhóm Củ", icon: "🥕", color: "bg-amber-500", light: "bg-amber-50 text-amber-700" },
      "Fruits": { nameEn: "Fruits", nameVn: "Nhóm Trái Cây", icon: "🍈", color: "bg-purple-500", light: "bg-purple-50 text-purple-700" },
      "Mushrooms": { nameEn: "Mushrooms", nameVn: "Nhóm Nấm", icon: "🍄", color: "bg-orange-500", light: "bg-orange-50 text-orange-700" },
      "Dairy": { nameEn: "Dairy & Yogurt", nameVn: "Sữa Chua", icon: "🥛", color: "bg-cyan-500", light: "bg-cyan-50 text-cyan-700" }
    };

    function App() {
      const [items, setItems] = useState([]);
      const [loading, setLoading] = useState(true);
      const [cart, setCart] = useState({});
      const [activeCategory, setActiveCategory] = useState("ALL");
      const [searchQuery, setSearchQuery] = useState("");
      const [showModal, setShowModal] = useState(false);
      const [copied, setCopied] = useState(false);

      useEffect(() => {
        fetch(OPEN_SHEET_URL)
          .then((res) => res.json())
          .then((data) => {
            const parsed = data.map((row, idx) => ({
              id: idx + 1,
              category: row["Category"] || "Leafy Greens",
              nameVn: row["Vietnamese Name"] || row["Tên hàng"] || "",
              nameEn: row["English Name"] || row["Vietnamese Name"] || "",
              weight: row["Unit Specification"] || row["Quy cách"] || "500 gr",
              price: parseInt(row["Price (VND)"] || row["Giá bán"] || 0, 10),
            })).filter(item => item.nameVn && item.price > 0);

            setItems(parsed);
            setLoading(false);
          })
          .catch((err) => {
            console.error("Failed to load live sheet data:", err);
            setLoading(false);
          });
      }, []);

      const handleQuantityChange = (id, delta) => {
        setCart((prev) => {
          const current = prev[id] || 0;
          const updated = Math.max(0, current + delta);
          if (updated === 0) {
            const copy = { ...prev };
            delete copy[id];
            return copy;
          }
          return { ...prev, [id]: updated };
        });
      };

      const totalItems = useMemo(() => {
        return Object.values(cart).reduce((sum, qty) => sum + qty, 0);
      }, [cart]);

      const totalPrice = useMemo(() => {
        return Object.entries(cart).reduce((sum, [id, qty]) => {
          const item = items.find((i) => i.id === Number(id));
          return sum + (item ? item.price * qty : 0);
        }, 0);
      }, [cart, items]);

      const filteredItems = useMemo(() => {
        return items.filter((item) => {
          const matchesCat = activeCategory === "ALL" || item.category === activeCategory;
          const matchesSearch =
            item.nameEn.toLowerCase().includes(searchQuery.toLowerCase()) ||
            item.nameVn.toLowerCase().includes(searchQuery.toLowerCase());
          return matchesCat && matchesSearch;
        });
      }, [items, activeCategory, searchQuery]);

      const generateZaloMessage = () => {
        let msg = `Chào shop, mình muốn đặt hàng:\n`;
        Object.entries(cart).forEach(([id, qty]) => {
          const item = items.find((i) => i.id === Number(id));
          if (item) {
            msg += `- ${item.nameVn} (${item.weight}): x${qty}\n`;
          }
        });
        msg += `\nTổng cộng: ${totalPrice.toLocaleString('vi-VN')} VND\nCảm ơn shop!`;
        return msg;
      };

      const copyToClipboard = () => {
        navigator.clipboard.writeText(generateZaloMessage());
        setCopied(true);
        setTimeout(() => setCopied(false), 2500);
      };

      return (
        <div className="max-w-4xl mx-auto px-4 pt-6">
          <header className="text-center mb-6">
            <div className="inline-flex items-center gap-2 px-4 py-1.5 rounded-full bg-gradient-to-r from-pink-500 via-purple-500 to-indigo-500 text-white font-bold text-xs uppercase tracking-wider shadow-md mb-3">
              ✨ An Việt Mộc Fresh Produce
            </div>
            <h1 className="text-4xl md:text-5xl font-extrabold tracking-tight bg-clip-text text-transparent bg-gradient-to-r from-pink-600 via-purple-600 to-cyan-500 mb-2">
              Juicy Veggie Builder
            </h1>
            <p className="text-slate-600 font-semibold text-sm max-w-md mx-auto">
              Tap tiles to quickly pick your veggies, review your total pack count & price, then click to copy formatted Zalo message!
            </p>
            <p className="text-slate-400 italic text-xs mt-1">
              (Chạm vào các ô để chọn rau củ, xem tổng số gói & giá, sau đó bấm để sao chép tin nhắn Zalo!)
            </p>
          </header>

          <div className="relative mb-6">
            <input
              type="text"
              placeholder="Search by English or Vietnamese name..."
              value={searchQuery}
              onChange={(e) => setSearchQuery(e.target.value)}
              className="w-full pl-12 pr-4 py-3.5 rounded-2xl border-2 border-pink-200 focus:border-purple-400 focus:outline-none bg-white/90 shadow-sm text-slate-800 font-medium placeholder-slate-400 text-sm md:text-base transition-all"
            />
            <span className="absolute left-4 top-1/2 -translate-y-1/2 text-pink-400 text-xl">🔍</span>
          </div>

          <div className="flex gap-2 overflow-x-auto pb-4 mb-4 scrollbar-none">
            <button
              onClick={() => setActiveCategory("ALL")}
              className={`px-4 py-2.5 rounded-xl font-bold text-xs md:text-sm whitespace-nowrap transition-all flex items-center gap-1.5 shadow-sm ${
                activeCategory === "ALL"
                  ? "bg-slate-900 text-white scale-105"
                  : "bg-white text-slate-600 hover:bg-slate-100"
              }`}
            >
              🌈 All Items
            </button>
            {Object.keys(CATEGORY_MAP).map((catKey) => {
              const cat = CATEGORY_MAP[catKey];
              const isActive = activeCategory === catKey;
              return (
                <button
                  key={catKey}
                  onClick={() => setActiveCategory(catKey)}
                  className={`px-4 py-2.5 rounded-xl font-bold text-xs md:text-sm whitespace-nowrap transition-all flex items-center gap-1.5 shadow-sm ${
                    isActive
                      ? `${cat.color} text-white scale-105 shadow-md`
                      : `bg-white text-slate-600 hover:${cat.light}`
                  }`}
                >
                  <span>{cat.icon}</span>
                  <span>{cat.nameEn}</span>
                </button>
              );
            })}
          </div>

          {loading ? (
            <div className="text-center py-20">
              <div className="inline-block animate-spin text-4xl mb-3">🥦</div>
              <p className="text-slate-500 font-bold">Syncing live price list from Google Sheets...</p>
            </div>
          ) : (
            <div className="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 gap-3.5">
              {filteredItems.map((item) => {
                const qty = cart[item.id] || 0;
                const isSelected = qty > 0;
                const catInfo = CATEGORY_MAP[item.category] || { icon: "🌱", color: "bg-emerald-500" };

                return (
                  <div
                    key={item.id}
                    onClick={() => handleQuantityChange(item.id, 1)}
                    className={`rainbow-border ${isSelected ? "selected" : ""} bg-white rounded-2xl p-3.5 shadow-sm hover:shadow-md cursor-pointer flex flex-col justify-between relative border border-slate-100 transition-all select-none`}
                  >
                    <div className="flex items-center justify-between mb-2">
                      <span className="w-9 h-9 rounded-xl bg-slate-50 flex items-center justify-center text-xl shadow-inner">
                        {catInfo.icon}
                      </span>
                      <span className="text-[11px] font-bold text-slate-400 bg-slate-100 px-2 py-0.5 rounded-full">
                        {item.weight}
                      </span>
                    </div>

                    <div>
                      <h3 className="font-extrabold text-slate-800 text-sm leading-tight line-clamp-1">
                        {item.nameEn}
                      </h3>
                      <p className="text-slate-400 text-xs font-semibold italic line-clamp-1 mb-3">
                        {item.nameVn}
                      </p>
                    </div>

                    <div className="flex items-center justify-between mt-auto pt-2 border-t border-slate-50">
                      <span className="font-extrabold text-pink-600 text-xs md:text-sm">
                        {item.price.toLocaleString('vi-VN')} đ
                      </span>

                      {isSelected ? (
                        <div
                          onClick={(e) => e.stopPropagation()}
                          className="flex items-center bg-slate-900 text-white rounded-xl px-1.5 py-1 gap-1.5 shadow-md scale-105"
                        >
                          <button
                            onClick={() => handleQuantityChange(item.id, -1)}
                            className="w-5 h-5 rounded-lg bg-slate-800 hover:bg-slate-700 flex items-center justify-center font-bold text-xs text-pink-400 active:scale-95"
                          >
                            -
                          </button>
                          <span className="font-extrabold text-xs px-1 text-emerald-400">{qty}</span>
                          <button
                            onClick={() => handleQuantityChange(item.id, 1)}
                            className="w-5 h-5 rounded-lg bg-slate-800 hover:bg-slate-700 flex items-center justify-center font-bold text-xs text-pink-400 active:scale-95"
                          >
                            +
                          </button>
                        </div>
                      ) : (
                        <button className="w-7 h-7 rounded-xl bg-pink-50 hover:bg-pink-100 text-pink-600 flex items-center justify-center font-bold text-base transition-colors">
                          +
                        </button>
                      )}
                    </div>
                  </div>
                );
              })}
            </div>
          )}

          {totalItems > 0 && (
            <div className="fixed bottom-4 left-1/2 -translate-x-1/2 w-[92%] max-w-lg glass-nav border border-white/60 shadow-2xl rounded-3xl p-3.5 z-40 flex items-center justify-between gap-3 animate-bounce-short">
              <div className="flex items-center gap-3">
                <div className="relative">
                  <span className="w-12 h-12 rounded-2xl bg-gradient-to-tr from-pink-500 to-yellow-400 flex items-center justify-center text-2xl shadow-lg">
                    🛍️
                  </span>
                  <span className="absolute -top-1.5 -right-1.5 bg-slate-900 text-emerald-400 font-extrabold text-xs w-6 h-6 rounded-full flex items-center justify-center border-2 border-white shadow">
                    {totalItems}
                  </span>
                </div>
                <div>
                  <p className="text-[10px] font-extrabold text-slate-400 uppercase tracking-wider">
                    Total Order / Tổng đơn hàng
                  </p>
                  <p className="text-lg font-black text-slate-900">
                    {totalPrice.toLocaleString('vi-VN')} <span className="text-xs text-pink-600 font-bold">VND</span>
                  </p>
                </div>
              </div>

              <div className="flex items-center gap-2">
                <button
                  onClick={() => setCart({})}
                  className="p-2.5 rounded-xl text-slate-400 hover:text-rose-500 hover:bg-rose-50 transition-colors"
                  title="Clear Order"
                >
                  🗑️
                </button>
                <button
                  onClick={() => setShowModal(true)}
                  className="px-4 py-3 rounded-2xl bg-gradient-to-r from-pink-500 via-purple-600 to-indigo-600 text-white font-extrabold text-xs md:text-sm shadow-lg hover:brightness-110 active:scale-95 transition-all flex items-center gap-1.5"
                >
                  <span>🛍️ Review & Copy</span>
                  <span className="text-[10px] opacity-80">(Xem & Sao chép)</span>
                </button>
              </div>
            </div>
          )}

          {showModal && (
            <div className="fixed inset-0 bg-slate-900/60 backdrop-blur-sm z-50 flex items-center justify-center p-4">
              <div className="bg-white rounded-3xl p-6 max-w-md w-full shadow-2xl relative border border-slate-100 animate-in fade-in zoom-in duration-200">
                <button
                  onClick={() => setShowModal(false)}
                  className="absolute top-4 right-4 w-8 h-8 rounded-full bg-slate-100 text-slate-500 font-bold flex items-center justify-center hover:bg-slate-200"
                >
                  ✕
                </button>

                <div className="flex items-center gap-2 mb-4">
                  <span className="text-2xl">📋</span>
                  <div>
                    <h3 className="font-extrabold text-slate-900 text-lg">Your Zalo Order Message</h3>
                    <p className="text-xs text-slate-400 font-semibold">Tin nhắn đặt hàng Zalo của bạn</p>
                  </div>
                </div>

                <div className="bg-slate-50 rounded-2xl p-4 text-xs md:text-sm font-mono text-slate-700 whitespace-pre-wrap border border-slate-200 max-h-60 overflow-y-auto mb-5 leading-relaxed">
                  {generateZaloMessage()}
                </div>

                <div className="flex gap-3">
                  <button
                    onClick={() => setShowModal(false)}
                    className="flex-1 py-3.5 rounded-2xl bg-slate-100 font-bold text-slate-600 text-xs md:text-sm hover:bg-slate-200"
                  >
                    Back to Edit
                  </button>
                  <button
                    onClick={copyToClipboard}
                    className={`flex-1 py-3.5 rounded-2xl font-black text-xs md:text-sm shadow-lg transition-all text-white flex items-center justify-center gap-2 ${
                      copied ? "bg-emerald-500 scale-95" : "bg-gradient-to-r from-pink-500 to-purple-600 hover:brightness-110 active:scale-95"
                    }`}
                  >
                    {copied ? "✓ Copied to Clipboard!" : "📋 Copy Message for Zalo"}
                  </button>
                </div>
              </div>
            </div>
          )}
        </div>
      );
    }

    ReactDOM.render(<App />, document.getElementById('root'));
  </script>
</body>
</html>
