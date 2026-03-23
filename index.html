import React, { useState, useEffect } from 'react';
import { initializeApp } from 'firebase/app';
import { getAuth, signInAnonymously, signInWithCustomToken, onAuthStateChanged, signOut, GoogleAuthProvider, signInWithPopup } from 'firebase/auth';
import { getFirestore, doc, getDoc } from 'firebase/firestore';
import { Lock, Crown, LogIn, LogOut, Volume2, GraduationCap, Sparkles, BookText, Headphones } from 'lucide-react';

// --- Firebase 配置 ---
const firebaseConfig = JSON.parse(__firebase_config);
const app = initializeApp(firebaseConfig);
const auth = getAuth(app);
const db = getFirestore(app);
const appId = typeof __app_id !== 'undefined' ? __app_id : 'baewooja-korean-pro';

export default function App() {
  const [user, setUser] = useState(null);
  const [isPro, setIsPro] = useState(false);
  const [loading, setLoading] = useState(true);
  const [activeTab, setActiveTab] = useState('pronunciation'); // 預設在發音模組

  useEffect(() => {
    const initAuth = async () => {
      if (typeof __initial_auth_token !== 'undefined' && __initial_auth_token) {
        await signInWithCustomToken(auth, __initial_auth_token);
      } else {
        await signInAnonymously(auth);
      }
    };
    initAuth();

    const unsubscribe = onAuthStateChanged(auth, async (currentUser) => {
      setUser(currentUser);
      if (currentUser && !currentUser.isAnonymous) {
        const userDoc = await getDoc(doc(db, 'artifacts', appId, 'users', currentUser.uid, 'profile'));
        setIsPro(userDoc.exists() && userDoc.data().isPro);
      } else {
        setIsPro(false);
      }
      setLoading(false);
    });
    return () => unsubscribe();
  }, []);

  const handleLogin = async () => {
    const provider = new GoogleAuthProvider();
    await signInWithPopup(auth, provider);
  };

  const handleLogout = () => signOut(auth);

  const speak = (text) => {
    const utterance = new SpeechSynthesisUtterance(text);
    utterance.lang = 'ko-KR';
    window.speechSynthesis.speak(utterance);
  };

  // --- 付費牆組件 ---
  const ProSection = ({ children, isLocked, title }) => {
    if (!isLocked) return <div className="animate-in fade-in duration-500">{children}</div>;
    return (
      <div className="relative overflow-hidden rounded-3xl border-2 border-dashed border-sky-200 bg-white">
        <div className="filter blur-md pointer-events-none select-none p-8 opacity-40">
          {children}
        </div>
        <div className="absolute inset-0 z-10 flex flex-col items-center justify-center bg-white/40 backdrop-blur-[4px] p-6 text-center">
          <div className="bg-gradient-to-br from-amber-400 to-orange-500 p-4 rounded-full shadow-xl mb-4 text-white">
            <Crown size={32} className="animate-bounce" />
          </div>
          <h3 className="text-2xl font-black text-slate-800 mb-2">{title} 為 PRO 專屬</h3>
          <p className="text-slate-600 mb-6 max-w-xs">升級至 Pro 版本，即可解鎖所有生活單字模版、常用語練習及離線學習功能。</p>
          {!user || user.isAnonymous ? (
            <button onClick={handleLogin} className="flex items-center gap-2 bg-sky-600 hover:bg-sky-700 text-white px-8 py-3 rounded-full font-bold transition-all transform hover:scale-105 shadow-lg">
              <LogIn size={20} /> 登入並解鎖
            </button>
          ) : (
            <button className="bg-amber-500 hover:bg-amber-600 text-white px-8 py-3 rounded-full font-bold transition-all transform hover:scale-105 shadow-lg">
              立即升級 (Stripe 付款)
            </button>
          )}
        </div>
      </div>
    );
  };

  if (loading) return <div className="h-screen flex items-center justify-center text-sky-500 font-bold">載入學習資源中...</div>;

  return (
    <div className="min-h-screen bg-slate-50 font-sans">
      <nav className="bg-white/80 backdrop-blur-md border-b sticky top-0 z-50">
        <div className="max-w-5xl mx-auto px-4 h-16 flex items-center justify-between">
          <div className="flex items-center gap-2 font-black text-sky-600 text-xl">
            <GraduationCap className="w-8 h-8" />
            <span className="tracking-tighter uppercase">Baewooja</span>
          </div>
          <div className="flex items-center gap-4">
            {isPro && <span className="bg-amber-100 text-amber-700 px-3 py-1 rounded-full text-xs font-black flex items-center gap-1"><Sparkles size={12}/> PRO</span>}
            {(!user || user.isAnonymous) ? (
              <button onClick={handleLogin} className="text-sm font-bold bg-sky-600 text-white px-5 py-2 rounded-full hover:bg-sky-700 transition">登入</button>
            ) : (
              <button onClick={handleLogout} className="text-slate-400 hover:text-red-500 transition"><LogOut size={22}/></button>
            )}
          </div>
        </div>
      </nav>

      <main className="max-w-4xl mx-auto px-4 py-10 space-y-10">
        <div className="text-center space-y-2">
          <h1 className="text-3xl font-black text-slate-900">韓語全方位學習中心</h1>
          <p className="text-slate-500">從發音開始，逐步掌握地道韓語</p>
        </div>

        {/* 頂層分類標籤 */}
        <div className="flex bg-white p-1.5 rounded-2xl shadow-sm border overflow-x-auto no-scrollbar">
          {[
            { id: 'pronunciation', name: '發音模組 (Free)', icon: Headphones, pro: false },
            { id: 'vocabulary', name: '單字模版 (Pro)', icon: BookText, pro: true },
          ].map(tab => (
            <button
              key={tab.id}
              onClick={() => setActiveTab(tab.id)}
              className={`flex-1 min-w-[150px] py-4 rounded-xl text-sm font-bold transition-all flex items-center justify-center gap-2 ${
                activeTab === tab.id ? 'bg-sky-600 text-white shadow-md' : 'text-slate-500 hover:bg-slate-50'
              }`}
            >
              <tab.icon size={18} />
              {tab.name}
              {tab.pro && !isPro && <Lock size={14} className="opacity-50" />}
            </button>
          ))}
        </div>

        {/* 內容顯示區 */}
        <div className="min-h-[500px]">
          {activeTab === 'pronunciation' && (
            <div className="space-y-8 animate-in fade-in slide-in-from-bottom-4 duration-500">
              <section className="bg-white p-8 rounded-3xl border shadow-sm">
                <h2 className="text-xl font-black mb-6 text-sky-700">母音與子音 (全開放)</h2>
                <div className="grid grid-cols-5 md:grid-cols-10 gap-2">
                  {['ㅏ', 'ㅑ', 'ㅓ', 'ㅕ', 'ㅗ', 'ㅛ', 'ㅜ', 'ㅠ', 'ㅡ', 'ㅣ'].map(v => (
                    <button key={v} onClick={() => speak(v)} className="aspect-square bg-sky-50 rounded-xl flex items-center justify-center text-2xl font-bold text-sky-600 hover:bg-sky-100 border border-sky-100 transition-colors">
                      {v}
                    </button>
                  ))}
                </div>
              </section>

              <section className="bg-white p-8 rounded-3xl border shadow-sm">
                <h2 className="text-xl font-black mb-6 text-sky-700">互動拼讀模擬器</h2>
                <div className="flex flex-col items-center p-10 bg-slate-50 rounded-2xl border border-dashed border-slate-200">
                  <div className="text-8xl font-black text-sky-600 mb-6 drop-shadow-sm">가</div>
                  <p className="text-slate-400 text-center mb-6">您可以組合子音與母音並聽取發音</p>
                  <button onClick={() => speak('가')} className="bg-sky-500 text-white px-8 py-3 rounded-full font-bold flex items-center gap-2 hover:bg-sky-600 transition shadow-lg">
                    <Volume2 size={20} /> 播放發音
                  </button>
                </div>
              </section>
            </div>
          )}

          {activeTab === 'vocabulary' && (
            <ProSection isLocked={!isPro} title="生活單字模版">
              <div className="grid md:grid-cols-2 gap-6 animate-in zoom-in-95 duration-500">
                <div className="bg-white p-8 rounded-3xl border border-slate-100 shadow-sm hover:shadow-md transition-shadow">
                  <div className="text-sky-500 font-black mb-1">水果篇 🍎</div>
                  <div className="text-2xl font-bold text-slate-800 mb-4">사과 (Sa-gwa)</div>
                  <div className="text-slate-500 text-sm">意思：蘋果</div>
                  <button onClick={() => speak('사과')} className="mt-4 text-sky-600 font-bold flex items-center gap-1 hover:underline">
                    <Volume2 size={16} /> 聽音
                  </button>
                </div>

                <div className="bg-white p-8 rounded-3xl border border-slate-100 shadow-sm hover:shadow-md transition-shadow">
                  <div className="text-sky-500 font-black mb-1">日常用語 👋</div>
                  <div className="text-2xl font-bold text-slate-800 mb-4">안녕하세요 (An-nyeong)</div>
                  <div className="text-slate-500 text-sm">意思：你好</div>
                  <button onClick={() => speak('안녕하세요')} className="mt-4 text-sky-600 font-bold flex items-center gap-1 hover:underline">
                    <Volume2 size={16} /> 聽音
                  </button>
                </div>
                
                {/* 更多單字卡片... */}
              </div>
            </ProSection>
          )}
        </div>
      </main>

      <footer className="text-center py-12 text-slate-400 text-sm border-t mt-10">
        <p>© 2026 Baewooja Korlearners. 韓語學習的最佳選擇</p>
      </footer>
    </div>
  );
}
