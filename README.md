import React, { useState } from 'react';
import { 
  CalendarDaysIcon, 
  TicketIcon, 
  BanknotesIcon, 
  BookOpenIcon, 
  ChevronRightIcon,
  MapPinIcon
} from '@heroicons/react/24/outline';

export default function TravelApp() {
  const [activeTab, setActiveTab] = useState('expense');

  return (
    <div className="min-h-screen bg-[#F7F4EB] text-[#5D574F] pb-24 font-sans select-none">
      {/* 頂部 Header */}
      <header className="p-6 pt-10 flex justify-between items-end">
        <div>
          <h1 className="text-2xl font-bold">京阪神之行 🇯🇵</h1>
          <p className="text-sm opacity-60">2026.06.02 - 06.07</p>
        </div>
        <div className="bg-orange-100 px-4 py-2 rounded-2xl border-2 border-orange-200">
          <span className="text-[10px] block font-bold text-orange-500">COUNTDOWN</span>
          <span className="text-xl font-bold text-orange-600 tracking-tighter text-center">D-12</span>
        </div>
      </header>

      {/* 主要內容區 */}
      <main className="px-5 space-y-6">
        
        {/* 記帳摘要儀表板 */}
        <section className="bg-white rounded-[2rem] p-6 shadow-[4px_4px_0px_#E0E5D5] border border-gray-100">
          <div className="flex justify-between items-start mb-4">
            <div>
              <p className="text-xs font-bold text-gray-400">總支出總計</p>
              <h2 className="text-3xl font-black text-gray-800">NT$ 25,316</h2>
            </div>
            <div className="bg-green-50 text-green-600 px-3 py-1 rounded-full text-xs font-bold border border-green-100">
              匯率 0.21
            </div>
          </div>
          <div className="flex gap-2">
            <div className="flex-1 bg-blue-50 p-3 rounded-2xl border border-blue-100">
              <p className="text-[10px] text-blue-400 font-bold uppercase">住宿</p>
              <p className="font-bold">NT$ 7,036</p>
            </div>
            <div className="flex-1 bg-orange-50 p-3 rounded-2xl border border-orange-100">
              <p className="text-[10px] text-orange-400 font-bold uppercase">票券</p>
              <p className="font-bold">NT$ 7,896</p>
            </div>
          </div>
        </section>

        {/* 記帳列表 (依照截圖樣式) */}
        <section className="space-y-4">
          <div className="flex justify-between items-center px-2">
            <h3 className="font-bold flex items-center gap-2">
              <BanknotesIcon className="w-5 h-5" /> 支出明細清單
            </h3>
            <span className="text-xs text-gray-400 font-medium">篩選日程</span>
          </div>

          <div className="space-y-3">
            {[
              { title: '阿倍野展望台', tag: '景點門票', amount: '376', color: 'orange' },
              { title: '機票 (樂桃航空)', tag: '交通接駁', amount: '13,920', color: 'green' },
              { title: 'blue shIMANOUCHI 訂金', tag: '住宿裝備', amount: '7,036', color: 'blue' },
              { title: '日本環球影城門票 (USJ)', tag: '景點門票', amount: '4,020', color: 'orange' }
            ].map((item, idx) => (
              <div key={idx} className="bg-white rounded-3xl p-4 flex items-center justify-between shadow-[4px_4px_0px_#E0E5D5] active:translate-x-0.5 active:translate-y-0.5 active:shadow-none transition-all cursor-pointer">
                <div className="flex items-center gap-4">
                  <div className={`w-12 h-12 rounded-2xl bg-${item.color}-50 flex items-center justify-center`}>
                    <MapPinIcon className={`w-6 h-6 text-${item.color}-500`} />
                  </div>
                  <div>
                    <h4 className="text-sm font-bold truncate w-32">{item.title}</h4>
                    <span className={`text-[10px] font-bold px-2 py-0.5 rounded-lg bg-${item.color}-100 text-${item.color}-600 uppercase`}>
                      {item.tag}
                    </span>
                  </div>
                </div>
                <div className="text-right">
                  <div className="text-sm font-black tracking-tight">NT$ {item.amount}</div>
                  <div className="text-[10px] text-gray-400 font-medium tracking-wider">YY (你) 付款</div>
                </div>
              </div>
            ))}
          </div>
        </section>
      </main>

      {/* 底部導航欄 */}
      <nav className="fixed bottom-6 left-1/2 -translate-x-1/2 w-[92%] max-w-md bg-white/90 backdrop-blur-xl rounded-[2.5rem] p-3 flex justify-around items-center shadow-2xl border border-white/50 ring-1 ring-black/5">
        <NavBtn active={activeTab === 'sch'} icon={<CalendarDaysIcon className="w-6 h-6"/>} label="行程" />
        <NavBtn active={activeTab === 'exp'} icon={<BanknotesIcon className="w-6 h-6"/>} label="記帳" />
        <div className="bg-orange-400 p-4 rounded-full shadow-lg shadow-orange-200 -mt-10 border-4 border-[#F7F4EB] active:scale-90 transition-transform">
          <span className="text-white text-2xl font-bold">+</span>
        </div>
        <NavBtn active={activeTab === 'book'} icon={<TicketIcon className="w-6 h-6"/>} label="預訂" />
        <NavBtn active={activeTab === 'log'} icon={<BookOpenIcon className="w-6 h-6"/>} label="日誌" />
      </nav>
    </div>
  );
}

function NavBtn({ icon, label, active }: any) {
  return (
    <button className={`flex flex-col items-center transition-colors ${active ? 'text-orange-500 font-bold' : 'text-gray-400'}`}>
      {icon}
      <span className="text-[10px] mt-1">{label}</span>
    </button>
  );
}# osaka
