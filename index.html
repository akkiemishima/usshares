import { useState, useCallback, useRef } from "react";
import { BarChart, Bar, Cell, XAxis, YAxis, Tooltip, ResponsiveContainer, ReferenceLine } from "recharts";

// ── CSS変数（積み立てシミュレーターと同じカラー）──────────────
const C = {
  cream:       "#fdf8f3",
  cream2:      "#f7f0e8",
  cream3:      "#efe5d8",
  coral:       "#e8816a",
  coralDark:   "#d4624a",
  coralLight:  "#f5c4b8",
  coralPale:   "#fdf0ec",
  mint:        "#5ba89a",
  mintLight:   "#a8d5ce",
  mintPale:    "#eef7f5",
  gold:        "#c9963a",
  goldPale:    "#fdf3e3",
  text:        "#3d2c2c",
  text2:       "#7a6060",
  text3:       "#b09a9a",
  shadow:      "rgba(180,120,100,0.12)",
  shadow2:     "rgba(180,120,100,0.22)",
};

// ── S&P500年次指数 ──────────────────────────────────────────
const SP500_INDEX = {
  2005:1.000,2006:1.136,2007:1.196,2008:0.752,
  2009:0.952,2010:1.094,2011:1.116,2012:1.293,
  2013:1.712,2014:1.946,2015:1.972,2016:2.209,
  2017:2.693,2018:2.577,2019:3.385,2020:4.006,
  2021:5.150,2022:4.215,2023:5.330,2024:6.690,
  2025:7.400,
};

// ── 銘柄プール ───────────────────────────────────────────────
const POOL = [
  // ACTIVE
  {t:"AAPL", n:"Apple",           p05:5.1,  p25:211,  s:"Tech",    status:"active"},
  {t:"MSFT", n:"Microsoft",       p05:24,   p25:420,  s:"Tech",    status:"active"},
  {t:"AMZN", n:"Amazon",          p05:44,   p25:210,  s:"Tech",    status:"active"},
  {t:"GOOGL",n:"Alphabet",        p05:190,  p25:175,  s:"Tech",    status:"active"},
  {t:"NVDA", n:"NVIDIA",          p05:1.5,  p25:1150, s:"Tech",    status:"active"},
  {t:"NFLX", n:"Netflix",         p05:3,    p25:870,  s:"Tech",    status:"active"},
  {t:"AMD",  n:"AMD",             p05:19,   p25:170,  s:"Tech",    status:"active"},
  {t:"CRM",  n:"Salesforce",      p05:8.5,  p25:295,  s:"Tech",    status:"active"},
  {t:"ADBE", n:"Adobe",           p05:28,   p25:450,  s:"Tech",    status:"active"},
  {t:"ORCL", n:"Oracle",          p05:13,   p25:165,  s:"Tech",    status:"active"},
  {t:"INTC", n:"Intel",           p05:26,   p25:22,   s:"Tech",    status:"active"},
  {t:"IBM",  n:"IBM",             p05:82,   p25:228,  s:"Tech",    status:"active"},
  {t:"CSCO", n:"Cisco",           p05:17,   p25:58,   s:"Tech",    status:"active"},
  {t:"QCOM", n:"Qualcomm",        p05:38,   p25:175,  s:"Tech",    status:"active"},
  {t:"TXN",  n:"Texas Instr.",    p05:28,   p25:195,  s:"Tech",    status:"active"},
  {t:"AVGO", n:"Broadcom",        p05:18,   p25:1600, s:"Tech",    status:"active"},
  {t:"META", n:"Meta",            p05:null, p25:590,  s:"Tech",    status:"active", ipo:2012,ip:38},
  {t:"TSLA", n:"Tesla",           p05:null, p25:280,  s:"Auto",    status:"active", ipo:2010,ip:17},
  {t:"NOW",  n:"ServiceNow",      p05:null, p25:920,  s:"Tech",    status:"active", ipo:2012,ip:55},
  {t:"CRWD", n:"CrowdStrike",     p05:null, p25:310,  s:"Tech",    status:"active", ipo:2019,ip:34},
  {t:"NET",  n:"Cloudflare",      p05:null, p25:95,   s:"Tech",    status:"active", ipo:2019,ip:15},
  {t:"DDOG", n:"Datadog",         p05:null, p25:120,  s:"Tech",    status:"active", ipo:2019,ip:27},
  {t:"JPM",  n:"JPMorgan",        p05:38,   p25:238,  s:"Finance", status:"active"},
  {t:"GS",   n:"Goldman Sachs",   p05:120,  p25:600,  s:"Finance", status:"active"},
  {t:"MS",   n:"Morgan Stanley",  p05:56,   p25:108,  s:"Finance", status:"active"},
  {t:"BRK.B",n:"Berkshire B",     p05:88,   p25:460,  s:"Finance", status:"active"},
  {t:"AXP",  n:"Amex",            p05:52,   p25:298,  s:"Finance", status:"active"},
  {t:"V",    n:"Visa",            p05:null, p25:330,  s:"Finance", status:"active", ipo:2008,ip:44},
  {t:"MA",   n:"Mastercard",      p05:null, p25:500,  s:"Finance", status:"active", ipo:2006,ip:39},
  {t:"SPGI", n:"S&P Global",      p05:18,   p25:490,  s:"Finance", status:"active"},
  {t:"BLK",  n:"BlackRock",       p05:130,  p25:1000, s:"Finance", status:"active"},
  {t:"BAC",  n:"Bank of America", p05:46,   p25:44,   s:"Finance", status:"active"},
  {t:"WFC",  n:"Wells Fargo",     p05:60,   p25:74,   s:"Finance", status:"active"},
  {t:"BX",   n:"Blackstone",      p05:null, p25:160,  s:"Finance", status:"active", ipo:2007,ip:31},
  {t:"KKR",  n:"KKR",             p05:null, p25:125,  s:"Finance", status:"active", ipo:2010,ip:8},
  {t:"PYPL", n:"PayPal",          p05:null, p25:75,   s:"Finance", status:"active", ipo:2015,ip:46},
  {t:"JNJ",  n:"J&J",             p05:62,   p25:155,  s:"Health",  status:"active"},
  {t:"UNH",  n:"UnitedHealth",    p05:55,   p25:510,  s:"Health",  status:"active"},
  {t:"LLY",  n:"Eli Lilly",       p05:55,   p25:820,  s:"Health",  status:"active"},
  {t:"MRK",  n:"Merck",           p05:29,   p25:103,  s:"Health",  status:"active"},
  {t:"ABBV", n:"AbbVie",          p05:null, p25:185,  s:"Health",  status:"active", ipo:2013,ip:29},
  {t:"TMO",  n:"Thermo Fisher",   p05:38,   p25:550,  s:"Health",  status:"active"},
  {t:"ISRG", n:"Intuitive Surg.", p05:35,   p25:510,  s:"Health",  status:"active"},
  {t:"DHR",  n:"Danaher",         p05:30,   p25:250,  s:"Health",  status:"active"},
  {t:"PFE",  n:"Pfizer",          p05:25,   p25:27,   s:"Health",  status:"active"},
  {t:"XOM",  n:"ExxonMobil",      p05:57,   p25:115,  s:"Energy",  status:"active"},
  {t:"CVX",  n:"Chevron",         p05:56,   p25:158,  s:"Energy",  status:"active"},
  {t:"COP",  n:"ConocoPhillips",  p05:33,   p25:115,  s:"Energy",  status:"active"},
  {t:"WMT",  n:"Walmart",         p05:45,   p25:95,   s:"Retail",  status:"active"},
  {t:"COST", n:"Costco",          p05:38,   p25:870,  s:"Retail",  status:"active"},
  {t:"HD",   n:"Home Depot",      p05:40,   p25:370,  s:"Retail",  status:"active"},
  {t:"TGT",  n:"Target",          p05:55,   p25:140,  s:"Retail",  status:"active"},
  {t:"MCD",  n:"McDonald's",      p05:31,   p25:285,  s:"Consumer",status:"active"},
  {t:"SBUX", n:"Starbucks",       p05:11,   p25:80,   s:"Consumer",status:"active"},
  {t:"NKE",  n:"Nike",            p05:12,   p25:75,   s:"Consumer",status:"active"},
  {t:"KO",   n:"Coca-Cola",       p05:42,   p25:72,   s:"Consumer",status:"active"},
  {t:"PEP",  n:"PepsiCo",         p05:59,   p25:148,  s:"Consumer",status:"active"},
  {t:"PG",   n:"P&G",             p05:54,   p25:168,  s:"Consumer",status:"active"},
  {t:"PM",   n:"Philip Morris",   p05:null, p25:130,  s:"Consumer",status:"active", ipo:2008,ip:47},
  {t:"DIS",  n:"Disney",          p05:28,   p25:100,  s:"Media",   status:"active"},
  {t:"CMCSA",n:"Comcast",         p05:17,   p25:40,   s:"Media",   status:"active"},
  {t:"BA",   n:"Boeing",          p05:60,   p25:185,  s:"Indust.", status:"active"},
  {t:"CAT",  n:"Caterpillar",     p05:47,   p25:355,  s:"Indust.", status:"active"},
  {t:"HON",  n:"Honeywell",       p05:35,   p25:205,  s:"Indust.", status:"active"},
  {t:"LMT",  n:"Lockheed",        p05:60,   p25:555,  s:"Indust.", status:"active"},
  {t:"DE",   n:"Deere",           p05:60,   p25:390,  s:"Indust.", status:"active"},
  {t:"GE",   n:"GE",              p05:36,   p25:195,  s:"Indust.", status:"active"},
  {t:"NEE",  n:"NextEra Energy",  p05:12,   p25:73,   s:"Utility", status:"active"},
  {t:"AMT",  n:"American Tower",  p05:22,   p25:200,  s:"REIT",    status:"active"},
  {t:"TMUS", n:"T-Mobile",        p05:null, p25:195,  s:"Telecom", status:"active", ipo:2007,ip:14},
  {t:"VZ",   n:"Verizon",         p05:33,   p25:44,   s:"Telecom", status:"active"},
  {t:"UPS",  n:"UPS",             p05:76,   p25:125,  s:"Logist.", status:"active"},
  {t:"FDX",  n:"FedEx",           p05:90,   p25:270,  s:"Logist.", status:"active"},
  // BANKRUPT
  {t:"LEH",      n:"Lehman Brothers",     p05:60,   s:"Finance", status:"bankrupt", bankrupt_year:2008, note:"リーマンショックで破綻・$0"},
  {t:"WAMUQ",    n:"Washington Mutual",   p05:42,   s:"Finance", status:"bankrupt", bankrupt_year:2008, note:"史上最大の銀行破綻・$0"},
  {t:"KMRT",     n:"Kmart",              p05:18,   s:"Retail",  status:"bankrupt", bankrupt_year:2018, note:"2018年破産申請・$0"},
  {t:"SHLDQ",    n:"Sears",              p05:55,   s:"Retail",  status:"bankrupt", bankrupt_year:2018, note:"2018年破産申請・$0"},
  {t:"RADIOSHACK",n:"RadioShack",        p05:30,   s:"Retail",  status:"bankrupt", bankrupt_year:2015, note:"2015年破産・$0"},
  {t:"EK",       n:"Kodak",             p05:28,   s:"Tech",    status:"bankrupt", bankrupt_year:2012, note:"デジタル化対応失敗・$0"},
  {t:"MBIA",     n:"MBIA Inc.",         p05:68,   s:"Finance", status:"bankrupt", bankrupt_year:2008, note:"金融危機で実質破綻・$0"},
  {t:"GT.ADV",   n:"GT Advanced Tech",  p05:null, s:"Tech",    status:"bankrupt", bankrupt_year:2014, ipo:2006,ip:8, note:"Apple契約失敗→破産・$0"},
  {t:"AHM",      n:"Am. Home Mortgage", p05:28,   s:"Finance", status:"bankrupt", bankrupt_year:2007, note:"サブプライム危機・$0"},
  // ACQUIRED_CASH
  {t:"BSC",  n:"Bear Stearns",     p05:130,  s:"Finance",  status:"acquired_cash", acq_year:2008,acq_price:10,   note:"JPMorganが$10/株で救済買収"},
  {t:"WFM",  n:"Whole Foods",      p05:12,   s:"Retail",   status:"acquired_cash", acq_year:2017,acq_price:42,   note:"Amazonが$42/株で買収"},
  {t:"LNKD", n:"LinkedIn",         p05:null, s:"Tech",     status:"acquired_cash", ipo:2011,ip:45, acq_year:2016,acq_price:196, note:"Microsoftが$196/株で買収"},
  {t:"TWX",  n:"Time Warner",      p05:35,   s:"Media",    status:"acquired_cash", acq_year:2018,acq_price:107,  note:"AT&Tが$107/株で買収"},
  {t:"MON",  n:"Monsanto",         p05:55,   s:"Health",   status:"acquired_cash", acq_year:2018,acq_price:128,  note:"Bayerが$128/株で買収"},
  {t:"CELG", n:"Celgene",          p05:28,   s:"Health",   status:"acquired_cash", acq_year:2019,acq_price:102,  note:"BMS(Bristol-Myers)が買収"},
  {t:"YHOO", n:"Yahoo!",           p05:38,   s:"Tech",     status:"acquired_cash", acq_year:2017,acq_price:48,   note:"Verizonが$48/株で買収"},
  {t:"TWC",  n:"Time Warner Cable",p05:38,   s:"Media",    status:"acquired_cash", acq_year:2016,acq_price:195,  note:"Charterが$195/株で買収"},
  {t:"SUNW", n:"Sun Microsystems", p05:4,    s:"Tech",     status:"acquired_cash", acq_year:2010,acq_price:9.5,  note:"Oracleが$9.5/株で買収"},
  {t:"DELL2",n:"Dell(旧上場)",     p05:38,   s:"Tech",     status:"acquired_cash", acq_year:2013,acq_price:13.65,note:"MBO・非上場化→$13.65/株"},
  {t:"BRCM", n:"Broadcom(旧)",     p05:17,   s:"Tech",     status:"acquired_cash", acq_year:2016,acq_price:54,   note:"Avagoが$54/株で買収"},
  // ACQUIRED_STOCK
  {t:"CFC",  n:"Countrywide Fin.", p05:35,   s:"Finance", status:"acquired_stock", acq_year:2008,acq_ratio:0.1822,acquirer:"BAC",acquirer_p25:44,  note:"BofAが株式交換で救済買収"},
  {t:"MER",  n:"Merrill Lynch",    p05:56,   s:"Finance", status:"acquired_stock", acq_year:2009,acq_ratio:0.8595,acquirer:"BAC",acquirer_p25:44,  note:"BofAが0.8595株で買収"},
  {t:"WB",   n:"Wachovia",         p05:45,   s:"Finance", status:"acquired_stock", acq_year:2009,acq_ratio:0.1991,acquirer:"WFC",acquirer_p25:74,  note:"Wells Fargoが0.1991株で買収"},
];

const ELIGIBLE = POOL.filter(s => s.p05 || s.ip);

function calcStockValue(stock, invest=1000) {
  const buyPrice = stock.p05 || stock.ip;
  if (!buyPrice) return null;
  const shares = invest / buyPrice;
  if (stock.status === "active")         return {value: shares * stock.p25,                                                   fate:"active"};
  if (stock.status === "bankrupt")       return {value: 0,                                                                    fate:"bankrupt"};
  if (stock.status === "acquired_cash")  return {value: (shares * stock.acq_price / (SP500_INDEX[stock.acq_year]||1)) * SP500_INDEX[2025], fate:"acquired_cash"};
  if (stock.status === "acquired_stock") return {value: shares * stock.acq_ratio * stock.acquirer_p25,                       fate:"acquired_stock"};
  return {value:0, fate:"unknown"};
}

function randomSample(arr, n) {
  const copy=[...arr]; const result=[];
  for(let i=0;i<n&&copy.length;i++){const idx=Math.floor(Math.random()*copy.length);result.push(copy.splice(idx,1)[0]);}
  return result;
}
function runTrial(pool) {
  const picked = randomSample(pool, 50);
  let total = 0;
  const details = picked.map(s=>{const r=calcStockValue(s);total+=r?r.value:0;return{...s,result:r};});
  return {total,details};
}

const fmt = n => n>=1000000?`$${(n/1000000).toFixed(2)}M`:`$${Math.round(n/1000)}K`;
const fmtFull = n => "$"+Math.round(n).toLocaleString();
const SP500_20Y = 50000 * SP500_INDEX[2025];

function percentile(sorted, p) {
  return sorted[Math.min(Math.floor(sorted.length*p/100),sorted.length-1)].total;
}

const FATE_LABEL = {
  active:"存続", acquired_cash:"現金買収→S&P再投資",
  acquired_stock:"株式交換→継続保有", bankrupt:"倒産・$0",
};
const FATE_COLOR = {
  active:C.mint, acquired_cash:C.gold, acquired_stock:C.mintLight, bankrupt:C.coral,
};

// ── カードコンポーネント ─────────────────────────────────────
const Card = ({children, style={}}) => (
  <div style={{background:"#fff",borderRadius:20,padding:"20px",marginBottom:12,
    boxShadow:`0 2px 16px ${C.shadow}`,transition:"box-shadow 0.2s",...style}}>
    {children}
  </div>
);

export default function App() {
  const [trials, setTrials]   = useState(500);
  const [results, setResults] = useState(null);
  const [running, setRunning] = useState(false);
  const [progress, setProgress] = useState(0);
  const [selected, setSelected] = useState(null);
  const [tab, setTab]         = useState("stats");
  const [includeNvda, setIncludeNvda] = useState(true);
  const [includeNflx, setIncludeNflx] = useState(true);
  const rafRef = useRef(null);

  const run = useCallback(()=>{
    setRunning(true); setResults(null); setSelected(null); setProgress(0);
    const pool = ELIGIBLE.filter(s =>
      (includeNvda || s.t !== "NVDA") &&
      (includeNflx || s.t !== "NFLX")
    );
    const CHUNK=50; let done=0; const all=[];
    function step(){
      const end=Math.min(done+CHUNK,trials);
      for(let i=done;i<end;i++) all.push(runTrial(pool));
      done=end; setProgress(Math.round(done/trials*100));
      if(done<trials){rafRef.current=requestAnimationFrame(step);}
      else{
        all.sort((a,b)=>a.total-b.total);
        const totals=all.map(r=>r.total);
        const mean=totals.reduce((s,v)=>s+v,0)/totals.length;
        const med=all[Math.floor(all.length/2)].total;
        const min=all[0].total; const max=all[all.length-1].total;
        const p10=percentile(all,10),p25=percentile(all,25),p75=percentile(all,75),p90=percentile(all,90);
        const beatSP=totals.filter(v=>v>SP500_20Y).length;
        const BIN=28; const binW=(max-min)/BIN;
        const bins=Array.from({length:BIN},(_,i)=>({from:min+i*binW,to:min+(i+1)*binW,count:0,label:fmt(min+i*binW)}));
        totals.forEach(v=>{const bi=Math.min(Math.floor((v-min)/binW),BIN-1);bins[bi].count++;});
        let bankruptCount=0,cashCount=0,stockCount=0,activeCount=0;
        all.forEach(t=>t.details.forEach(d=>{
          if(d.result?.fate==="bankrupt")       bankruptCount++;
          else if(d.result?.fate==="acquired_cash")  cashCount++;
          else if(d.result?.fate==="acquired_stock") stockCount++;
          else activeCount++;
        }));
        setResults({all,totals,mean,med,min,max,p10,p25,p75,p90,beatSP,bins,binW,
          fateStats:{bankruptCount,cashCount,stockCount,activeCount,total:all.length*50}});
        setRunning(false);
      }
    }
    rafRef.current=requestAnimationFrame(step);
  },[trials, includeNvda, includeNflx]);

  return (
    <div style={{fontFamily:"'Zen Maru Gothic','Hiragino Sans',sans-serif",background:C.cream,
      color:C.text,minHeight:"100vh",paddingBottom:"3rem",
      backgroundImage:`radial-gradient(circle at 20% 20%, rgba(232,129,106,0.06) 0%, transparent 50%),
                       radial-gradient(circle at 80% 80%, rgba(91,168,154,0.06) 0%, transparent 50%)`}}>

      {/* ── プロフィールバー ── */}
      <div style={{background:`linear-gradient(135deg,${C.coral} 0%,${C.coralDark} 100%)`,
        color:"#fff",padding:"10px 1.2rem",display:"flex",alignItems:"center",gap:12}}>
        <div style={{fontSize:28,flexShrink:0}}>🌱</div>
        <div style={{flex:1}}>
          <div style={{fontSize:14,fontWeight:700}}>あっきー（三嶋義明）</div>
          <div style={{fontSize:11,opacity:0.88,lineHeight:1.6}}>
            計算オタク。なんでも計算してみないと気が済まない性格。『難しいお金の話も、優しく、易しく』をモットーにnoteで発信中。
          </div>
        </div>
        <a href="https://note.com/akkiemishima/n/n2894d229f980" target="_blank" rel="noopener noreferrer"
          style={{fontSize:11,fontWeight:700,color:"#fff",background:"rgba(255,255,255,0.22)",
            borderRadius:20,padding:"4px 12px",whiteSpace:"nowrap",textDecoration:"none",flexShrink:0}}>
          noteを読む
        </a>
      </div>

      <div style={{maxWidth:640,margin:"0 auto",padding:"0 1.2rem"}}>

        {/* ── ページタイトル・説明 ── */}
        <div style={{padding:"24px 0 8px",textAlign:"center"}}>
          <h1 style={{fontSize:"clamp(24px,5vw,32px)",fontWeight:700,color:C.text,lineHeight:1.4,marginBottom:8}}>
            米国株ランダム投資<br/>
            <span style={{color:C.coral}}>モンテカルロ</span>・シミュレーター
          </h1>
          {/* キャッチコピー */}
          <div style={{fontSize:15,fontWeight:700,color:C.mint,marginBottom:16,lineHeight:1.6}}>
            S&P500に負けない確率は何%？<br/>
            <span style={{fontSize:13,color:C.text3,fontWeight:400}}>ランダム50社選びを何千回も繰り返して検証する</span>
          </div>
          {/* SP500ベースライン表示 */}
          <Card style={{background:C.mintPale,boxShadow:"none",border:`1px solid ${C.mintLight}`,padding:"14px 18px",marginBottom:12,textAlign:"left"}}>
            <div style={{fontSize:13,fontWeight:700,color:C.mint,marginBottom:8}}>📊 比較基準：S&P500インデックスファンド（同期間）</div>
            <div style={{fontSize:15,color:C.text2,lineHeight:2.0}}>
              2005年〜2025年の<strong style={{color:C.text}}>20年間</strong>、S&P500に<strong style={{color:C.text}}>$50,000</strong>一括投資していたら<br/>
              <strong style={{color:C.mint,fontSize:20}}>{fmt(SP500_20Y)}</strong>
              <span style={{fontSize:14,color:C.text3,marginLeft:8}}>（×{(SP500_20Y/50000).toFixed(1)}倍 / CAGR 約10.5%）</span>
            </div>
          </Card>
          <Card style={{background:C.coralPale,boxShadow:"none",border:`1px solid ${C.coralLight}`,padding:"14px 18px",marginBottom:0,textAlign:"left"}}>
            <div style={{fontSize:14,color:C.text2,lineHeight:2.0}}>
              <strong style={{color:C.coral}}>このシミュレーターでできること：</strong><br/>
              同じ$50,000を、米国株<strong style={{color:C.text}}>ランダム50社×$1,000ずつ</strong>に分けて投資していたら？を何百回・何千回と試します。<br/>
              💀 倒産・$0銘柄、💵 現金買収→S&P500再投資、🔄 株式交換——すべて現実に即して計算。S&P500を上回れる確率が一目でわかります。
            </div>
          </Card>
        </div>

        {/* ── 大化け銘柄スイッチ ── */}
        <Card style={{marginTop:12, marginBottom:0}}>
          <div style={{fontSize:16,fontWeight:700,color:C.text2,marginBottom:10}}>
            🔥 100倍超え銘柄の参加設定
          </div>
          <div style={{fontSize:14,color:C.text3,marginBottom:14,lineHeight:1.9}}>
            スイッチをONにすると銘柄プールに含まれ、ランダム抽選の対象になります。OFFにするとプールから除外され、絶対に選ばれません。両方OFFにすると分布の形がどう変わるか試してみてください。
          </div>
          <div style={{display:"flex",flexDirection:"column",gap:10}}>
            {[
              {key:"nvda", label:"NVDA（NVIDIA）", sub:"$1,000 → $767,000（767倍）", val:includeNvda, set:setIncludeNvda},
              {key:"nflx", label:"NFLX（Netflix）", sub:"$1,000 → $290,000（290倍）", val:includeNflx, set:setIncludeNflx},
            ].map(item=>(
              <div key={item.key} style={{display:"flex",alignItems:"center",justifyContent:"space-between",
                background:item.val ? C.coralPale : C.cream2,
                borderRadius:12, padding:"16px 18px",
                border:`1px solid ${item.val ? C.coralLight : C.cream3}`,
                transition:"all 0.2s"}}>
                <div>
                  <div style={{fontSize:16,fontWeight:700,color:item.val ? C.coral : C.text3}}>{item.label}</div>
                  <div style={{fontSize:14,color:item.val ? C.coral : C.text3,opacity:0.8,marginTop:3}}>{item.sub}</div>
                </div>
                <div onClick={()=>item.set(v=>!v)} style={{
                  width:60,height:32,borderRadius:16,flexShrink:0,cursor:"pointer",
                  background:item.val ? C.coral : C.cream3,
                  position:"relative",transition:"background 0.25s",
                  boxShadow:item.val?`0 2px 8px rgba(232,129,106,0.4)`:"none",
                }}>
                  <div style={{
                    position:"absolute",width:26,height:26,borderRadius:"50%",
                    background:"#fff",top:3,
                    left:item.val ? 31 : 3,
                    transition:"left 0.25s",
                    boxShadow:"0 1px 4px rgba(0,0,0,0.15)",
                  }}/>
                </div>
              </div>
            ))}
          </div>
          {!includeNvda && !includeNflx && (
            <div style={{marginTop:12,padding:"14px 16px",background:C.mintPale,borderRadius:10,
              fontSize:14,color:C.mint,fontWeight:700,lineHeight:1.8}}>
              💡 両方OFFにすると分布の二山がなくなり、より正規分布に近くなります
            </div>
          )}
        </Card>

        {/* ── コントロール ── */}
        <Card style={{marginTop:12}}>
          <div style={{fontSize:16,fontWeight:700,color:C.text2,marginBottom:12}}>試行回数を選んで「RUN」を押してください</div>
          <div style={{display:"flex",flexWrap:"wrap",gap:8,marginBottom:16}}>
            {[100,500,1000].map(n=>(
              <button key={n} onClick={()=>setTrials(n)} style={{
                background:trials===n?C.coralPale:"transparent",
                border:`2px solid ${trials===n?C.coral:C.cream3}`,
                color:trials===n?C.coral:C.text3,
                padding:"12px 28px",borderRadius:12,cursor:"pointer",
                fontFamily:"inherit",fontSize:17,fontWeight:700,transition:"all 0.18s",
              }}>{n.toLocaleString()}回</button>
            ))}
          </div>
          <button onClick={run} disabled={running} style={{
            width:"100%",padding:"16px",borderRadius:12,border:"none",
            background:running?C.cream3:`linear-gradient(135deg,${C.coral} 0%,${C.coralDark} 100%)`,
            color:running?C.text3:"#fff",fontSize:17,fontFamily:"inherit",fontWeight:700,
            cursor:running?"not-allowed":"pointer",
            boxShadow:running?"none":`0 4px 16px rgba(232,129,106,0.4)`,
            transition:"opacity 0.2s",
          }}>
            {running?`計算中… ${progress}%`:"▶ シミュレーション開始"}
          </button>
          {running&&(
            <div style={{marginTop:12,height:6,background:C.cream3,borderRadius:3,overflow:"hidden"}}>
              <div style={{height:"100%",width:`${progress}%`,
                background:`linear-gradient(90deg,${C.coral},${C.gold})`,
                transition:"width 0.1s",borderRadius:3}}/>
            </div>
          )}
        </Card>

        {results&&(<>

          {/* ── メイン結果バナー ── */}
          <div style={{background:`linear-gradient(135deg,${C.coral} 0%,${C.coralDark} 100%)`,
            borderRadius:20,padding:"28px 24px",marginBottom:12,textAlign:"center",
            boxShadow:"0 6px 24px rgba(232,129,106,0.35)",color:"#fff",position:"relative",overflow:"hidden"}}>
            <div style={{position:"absolute",top:-30,right:-30,width:120,height:120,borderRadius:"50%",background:"rgba(255,255,255,0.08)"}}/>
            <div style={{fontSize:16,opacity:0.9,marginBottom:8,fontWeight:700,letterSpacing:"0.05em"}}>
              {trials.toLocaleString()}回試行の中央値
            </div>
            <div style={{fontSize:58,fontWeight:700,lineHeight:1.1,marginBottom:8}}>{fmt(results.med)}</div>
            <div style={{fontSize:18,opacity:0.9}}>
              元本$50,000 → <strong>×{(results.med/50000).toFixed(1)}倍</strong>
              <span style={{fontSize:15,opacity:0.8,marginLeft:12}}>平均値 {fmt(results.mean)}</span>
            </div>
          </div>

          {/* ── S&P500比較カード（独立） ── */}
          <Card style={{background:C.mintPale,boxShadow:"none",border:`1px solid ${C.mintLight}`,marginBottom:12}}>
            <div style={{fontSize:15,fontWeight:700,color:C.mint,marginBottom:12}}>📊 S&P500との比較</div>
            <div style={{display:"grid",gridTemplateColumns:"1fr 1fr",gap:12}}>
              <div style={{background:"#fff",borderRadius:14,padding:"16px",textAlign:"center"}}>
                <div style={{fontSize:13,color:C.text3,fontWeight:700,marginBottom:6}}>S&P500（同期間）</div>
                <div style={{fontSize:26,fontWeight:700,color:C.mint}}>{fmt(SP500_20Y)}</div>
                <div style={{fontSize:14,color:C.mint,opacity:0.8,marginTop:3}}>×{(SP500_20Y/50000).toFixed(1)}倍</div>
              </div>
              <div style={{background:"#fff",borderRadius:14,padding:"16px",textAlign:"center"}}>
                <div style={{fontSize:13,color:C.text3,fontWeight:700,marginBottom:6}}>S&P500超え率</div>
                <div style={{fontSize:26,fontWeight:700,color:C.coral}}>
                  {(results.beatSP/results.totals.length*100).toFixed(1)}%
                </div>
                <div style={{fontSize:13,color:C.text3,marginTop:3}}>
                  {results.beatSP.toLocaleString()} / {results.totals.length.toLocaleString()}試行
                </div>
              </div>
            </div>
          </Card>

          {/* ── 最頻レンジ ── */}
          {(()=>{
            const modebin = [...results.bins].sort((a,b)=>b.count-a.count)[0];
            const modePct = (modebin.count/results.totals.length*100).toFixed(1);
            return (
              <Card style={{background:C.goldPale,boxShadow:"none",border:`1px solid #e8d4a0`,
                textAlign:"center",padding:"20px",marginBottom:12}}>
                <div style={{fontSize:15,fontWeight:700,color:C.gold,marginBottom:10}}>📊 最頻レンジ（最も多かった結果）</div>
                <div style={{fontSize:32,fontWeight:700,color:C.text,marginBottom:6}}>
                  {fmt(modebin.from)} 〜 {fmt(modebin.to)}
                </div>
                <div style={{fontSize:15,color:C.text2}}>
                  全試行の <strong style={{color:C.gold,fontSize:22}}>{modePct}%</strong> がこのレンジに集中
                  <span style={{color:C.text3,fontSize:13,display:"block",marginTop:3}}>
                    {modebin.count.toLocaleString()}回 / {results.totals.length.toLocaleString()}回
                  </span>
                </div>
              </Card>
            );
          })()}

          {/* ── 統計カード8枚 ── */}
          <div style={{display:"grid",gridTemplateColumns:"1fr 1fr",gap:10,marginBottom:12}}>
            {[
              {label:"最大値",   val:fmt(results.max),  mult:(results.max/50000).toFixed(1),  color:C.coral},
              {label:"上位10%", val:fmt(results.p90),  mult:(results.p90/50000).toFixed(1),  color:C.coral},
              {label:"上位25%", val:fmt(results.p75),  mult:(results.p75/50000).toFixed(1),  color:C.mint},
              {label:"中央値",   val:fmt(results.med),  mult:(results.med/50000).toFixed(1),  color:C.mint},
              {label:"平均値",   val:fmt(results.mean), mult:(results.mean/50000).toFixed(1), color:C.gold},
              {label:"下位25%", val:fmt(results.p25),  mult:(results.p25/50000).toFixed(1),  color:C.text3},
              {label:"下位10%", val:fmt(results.p10),  mult:(results.p10/50000).toFixed(1),  color:C.text3},
              {label:"最小値",   val:fmt(results.min),  mult:(results.min/50000).toFixed(1),  color:C.text3},
            ].map(c=>(
              <div key={c.label} style={{background:"#fff",borderRadius:14,padding:"18px 16px",
                boxShadow:`0 2px 12px ${C.shadow}`,textAlign:"center"}}>
                <div style={{fontSize:13,color:C.text3,fontWeight:700,marginBottom:8,letterSpacing:"0.05em"}}>{c.label}</div>
                <div style={{fontSize:24,fontWeight:700,color:c.color}}>{c.val}</div>
                <div style={{fontSize:14,color:c.color,opacity:0.75,marginTop:4}}>×{c.mult}倍</div>
              </div>
            ))}
          </div>

          {/* ── 退場銘柄内訳 ── */}
          <Card style={{background:C.goldPale,boxShadow:"none",border:`1px solid #e8d4a0`,marginTop:0}}>
            <div style={{fontSize:15,fontWeight:700,color:C.gold,marginBottom:10}}>退場銘柄の内訳（全試行合計）</div>
            <div style={{display:"grid",gridTemplateColumns:"1fr 1fr",gap:8}}>
              {[
                {label:"💀 倒産・$0",            val:results.fateStats.bankruptCount, color:C.coral},
                {label:"💵 現金買収→SP再投資",   val:results.fateStats.cashCount,     color:C.gold},
                {label:"🔄 株式交換→継続保有",   val:results.fateStats.stockCount,    color:C.mint},
                {label:"✅ 存続",                 val:results.fateStats.activeCount,   color:C.text2},
              ].map(f=>(
                <div key={f.label} style={{background:"#fff",borderRadius:10,padding:"12px",textAlign:"center"}}>
                  <div style={{fontSize:13,color:C.text3,marginBottom:5,lineHeight:1.5}}>{f.label}</div>
                  <div style={{fontSize:18,fontWeight:700,color:f.color}}>
                    {f.val.toLocaleString()}
                    <span style={{fontSize:12,color:C.text3,marginLeft:4}}>
                      ({(f.val/results.fateStats.total*100).toFixed(1)}%)
                    </span>
                  </div>
                </div>
              ))}
            </div>
          </Card>

          {/* ── ヒストグラム ── */}
          <Card>
            <div style={{fontSize:15,fontWeight:700,color:C.text2,marginBottom:12}}>最終評価額の分布</div>
            <ResponsiveContainer width="100%" height={220}>
              <BarChart data={results.bins} margin={{top:4,right:4,left:-16,bottom:4}}>
                <XAxis dataKey="label" tick={{fill:C.text3,fontSize:10}} tickLine={false} axisLine={{stroke:C.cream3}} interval={5}/>
                <YAxis tick={{fill:C.text3,fontSize:10}} tickLine={false} axisLine={{stroke:C.cream3}}/>
                <Tooltip cursor={{fill:C.cream2}}
                  contentStyle={{background:"#fff",border:`1px solid ${C.cream3}`,borderRadius:10,fontSize:13,fontFamily:"inherit"}}
                  formatter={v=>[`${v}試行`,"頻度"]} labelFormatter={l=>`〜${l}`}/>
                <ReferenceLine
                  x={results.bins.find(b=>b.from<=SP500_20Y&&b.to>SP500_20Y)?.label}
                  stroke={C.mint} strokeDasharray="4 2" strokeWidth={1.5}/>
                <Bar dataKey="count" radius={[4,4,0,0]}>
                  {results.bins.map((b,i)=>{
                    const mid=b.from+results.binW/2;
                    const color=mid<results.p25?"#e8d4d4":mid<results.med?C.coralLight:mid<results.p75?C.mintLight:mid<results.p90?C.gold:C.coral;
                    return <Cell key={i} fill={color}/>;
                  })}
                </Bar>
              </BarChart>
            </ResponsiveContainer>
            <div style={{display:"flex",gap:12,flexWrap:"wrap",fontSize:12,color:C.text3,marginTop:10}}>
              {[
                {color:"#e8d4d4",label:"下位25%"},
                {color:C.coralLight,label:"25〜中央値"},
                {color:C.mintLight,label:"中央値〜75%"},
                {color:C.gold,label:"上位10〜25%"},
                {color:C.coral,label:"上位10%"},
              ].map(l=>(
                <span key={l.label} style={{display:"flex",alignItems:"center",gap:5,fontWeight:700}}>
                  <span style={{width:12,height:12,background:l.color,display:"inline-block",borderRadius:3}}/>
                  {l.label}
                </span>
              ))}
            </div>
          </Card>

          {/* ── タブ ── */}
          <div style={{display:"grid",gridTemplateColumns:"1fr 1fr",gap:6,background:C.cream2,
            padding:6,borderRadius:20,marginBottom:12}}>
            {[["stats","📊 全試行一覧"],["pool","📋 銘柄プール"]].map(([key,label])=>(
              <button key={key} onClick={()=>setTab(key)} style={{
                padding:"14px 6px",fontSize:15,fontWeight:700,fontFamily:"inherit",
                borderRadius:14,cursor:"pointer",textAlign:"center",border:"none",
                background:tab===key?"#fff":"transparent",
                color:tab===key?C.coral:C.text3,
                boxShadow:tab===key?`0 2px 12px ${C.shadow2}`:"none",
                transition:"all 0.2s",
              }}>{label}</button>
            ))}
          </div>

          {tab==="stats"&&(
            <Card>
              <div style={{fontSize:13,color:C.text3,marginBottom:10,fontWeight:700}}>
                マス目をタップして保有銘柄を確認
              </div>
              <div style={{display:"grid",gridTemplateColumns:"repeat(auto-fill,minmax(72px,1fr))",
                gap:4,maxHeight:280,overflowY:"auto"}}>
                {results.all.map((r,i)=>{
                  const ratio=r.total/results.med;
                  const col=ratio>=2?C.coral:ratio>=1.4?C.gold:ratio>=1?C.mint:C.text3;
                  const bg=ratio>=2?C.coralPale:ratio>=1.4?C.goldPale:ratio>=1?C.mintPale:C.cream2;
                  const isSel=selected?.idx===i;
                  return(
                    <div key={i} onClick={()=>setSelected(isSel?null:{...r,idx:i})} style={{
                      background:isSel?col+"30":bg,
                      border:`2px solid ${isSel?col:C.cream3}`,
                      padding:"6px 4px",cursor:"pointer",textAlign:"center",
                      borderRadius:10,transition:"all 0.15s",
                    }}>
                      <div style={{fontSize:8,color:C.text3}}>#{i+1}</div>
                      <div style={{fontSize:10,fontWeight:700,color:col}}>{fmt(r.total)}</div>
                    </div>
                  );
                })}
              </div>

              {selected&&(
                <div style={{marginTop:16,background:C.coralPale,borderRadius:16,padding:16}}>
                  <div style={{display:"flex",justifyContent:"space-between",marginBottom:12,flexWrap:"wrap",gap:8}}>
                    <div>
                      <span style={{fontSize:13,color:C.text3}}>試行 #{selected.idx+1}</span>
                      <span style={{fontSize:22,fontWeight:700,color:C.coral,marginLeft:10}}>{fmt(selected.total)}</span>
                      <span style={{fontSize:14,color:C.text3,marginLeft:6}}>×{(selected.total/50000).toFixed(1)}</span>
                    </div>
                    <button onClick={()=>setSelected(null)} style={{
                      background:C.cream3,border:"none",borderRadius:20,color:C.text3,
                      padding:"4px 12px",cursor:"pointer",fontFamily:"inherit",fontSize:13,fontWeight:700,
                    }}>✕ 閉じる</button>
                  </div>
                  <div style={{display:"grid",gridTemplateColumns:"repeat(auto-fill,minmax(130px,1fr))",gap:6}}>
                    {[...selected.details].sort((a,b)=>(b.result?.value||0)-(a.result?.value||0)).map(d=>{
                      const val=d.result?.value||0;
                      const fate=d.result?.fate||"unknown";
                      const col=FATE_COLOR[fate]||C.text3;
                      const mult=val/1000;
                      return(
                        <div key={d.t} style={{background:"#fff",borderRadius:12,padding:"10px 12px",
                          border:`1px solid ${C.cream3}`}}>
                          <div style={{display:"flex",justifyContent:"space-between",alignItems:"baseline"}}>
                            <span style={{fontSize:13,fontWeight:700,color:col}}>{d.t}</span>
                            <span style={{fontSize:10,color:col,opacity:0.8}}>{d.s}</span>
                          </div>
                          <div style={{fontSize:11,color:C.text3,marginBottom:4}}>{d.n}</div>
                          <div style={{fontSize:13,color:C.text,fontWeight:700}}>{fmtFull(val)}</div>
                          {fate==="bankrupt"
                            ?<div style={{fontSize:11,color:C.coral}}>💀 倒産（{d.bankrupt_year}）</div>
                            :fate==="acquired_cash"
                            ?<div style={{fontSize:11,color:C.gold}}>💵 買収→SP再投資</div>
                            :fate==="acquired_stock"
                            ?<div style={{fontSize:11,color:C.mint}}>🔄 {d.acquirer}株へ</div>
                            :<div style={{fontSize:11,color:C.mint}}>×{mult>=10?mult.toFixed(0):mult.toFixed(1)}</div>
                          }
                        </div>
                      );
                    })}
                  </div>
                </div>
              )}
            </Card>
          )}

          {tab==="pool"&&(
            <Card>
              <div style={{display:"grid",gridTemplateColumns:"repeat(auto-fill,minmax(190px,1fr))",
                gap:6,maxHeight:420,overflowY:"auto"}}>
                {ELIGIBLE.map(s=>{
                  const col=FATE_COLOR[s.status]||C.mint;
                  return(
                    <div key={s.t} style={{background:C.cream,borderRadius:12,padding:"10px 12px",
                      border:`1px solid ${C.cream3}`}}>
                      <div style={{display:"flex",justifyContent:"space-between"}}>
                        <span style={{fontWeight:700,color:col,fontSize:14}}>{s.t}</span>
                        <span style={{fontSize:11,color:C.text3}}>{s.s}</span>
                      </div>
                      <div style={{fontSize:12,color:C.text3,marginBottom:3}}>{s.n}</div>
                      {s.status==="active"
                        ?<div style={{fontSize:12,color:C.mint}}>
                          ${s.p05||s.ip} → ${s.p25}（×{((s.p25/(s.p05||s.ip)).toFixed(1))}）
                         </div>
                        :s.status==="bankrupt"
                        ?<div style={{fontSize:11,color:C.coral}}>💀 {s.note}</div>
                        :s.status==="acquired_cash"
                        ?<div style={{fontSize:9,color:C.gold}}>💵 {s.note}</div>
                        :<div style={{fontSize:9,color:C.mint}}>🔄 {s.note}</div>
                      }
                    </div>
                  );
                })}
              </div>
            </Card>
          )}

          {/* ── ディスクレーマー ── */}
          <div style={{fontSize:11,color:C.text3,lineHeight:1.9,background:C.cream2,
            borderRadius:12,padding:"14px 16px",marginTop:4}}>
            <p>※ 株価・買収価格は概算値。配当・税金・手数料は未考慮。</p>
            <p>※ S&P500再投資は買収年の指数比で計算。過去データに基づく参考値であり、将来の成果を保証するものではありません。</p>
          </div>
        </>)}

        {!results&&!running&&(
          <Card style={{textAlign:"center",padding:"48px 20px"}}>
            <div style={{fontSize:48,marginBottom:16}}>📊</div>
            <div style={{fontSize:15,fontWeight:700,color:C.text2,marginBottom:8}}>
              試行回数を選んで<br/>シミュレーション開始を押してください
            </div>
            <div style={{fontSize:12,color:C.text3,lineHeight:1.8}}>
              倒産・買収・大化け——すべてを含んだリアルな20年シミュレーション
            </div>
          </Card>
        )}
      </div>
    </div>
  );
}
