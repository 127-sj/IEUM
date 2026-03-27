import React, { useState, useEffect } from 'react';
import { 
  Train, 
  Sparkles, 
  Ticket, 
  Store, 
  HeartHandshake, 
  Menu, 
  X, 
  ChevronRight,
  Zap,
  Timer
} from 'lucide-react';

const App = () => {
  const [isMenuOpen, setIsMenuOpen] = useState(false);
  const [scrolled, setScrolled] = useState(false);

  useEffect(() => {
    const handleScroll = () => {
      setScrolled(window.scrollY > 50);
    };
    window.onscroll = handleScroll;
    return () => { window.onscroll = null; };
  }, []);

  const NavItem = ({ label, href }) => (
    <a href={href} className="text-gray-700 hover:text-blue-600 font-medium transition-colors">
      {label}
    </a>
  );

  return (
    <div className="min-h-screen bg-white font-sans text-gray-900 overflow-x-hidden">
      {/* Navigation */}
      <nav className={`fixed w-full z-50 transition-all duration-300 ${scrolled ? 'bg-white/90 backdrop-blur-md shadow-sm py-3' : 'bg-transparent py-5'}`}>
        <div className="max-w-7xl mx-auto px-6 flex justify-between items-center">
          <div className="flex items-center space-x-2">
            <Train className="w-8 h-8 text-blue-600" />
            <span className="text-2xl font-bold tracking-tighter text-blue-900">이음 (IEUM)</span>
          </div>
          
          <div className="hidden md:flex space-x-10">
            <NavItem label="여행 패스" href="#pass" />
            <NavItem label="특산물 직거래" href="#market" />
            <NavItem label="공동구매 펀딩" href="#funding" />
            <NavItem label="수익 모델" href="#business" />
          </div>

          <button className="hidden md:block bg-blue-600 text-white px-6 py-2 rounded-full font-semibold hover:bg-blue-700 transition-all shadow-lg shadow-blue-200">
            앱 실행하기
          </button>

          <button className="md:hidden" onClick={() => setIsMenuOpen(!isMenuOpen)}>
            {isMenuOpen ? <X /> : <Menu />}
          </button>
        </div>
      </nav>

      {/* Mobile Menu */}
      {isMenuOpen && (
        <div className="fixed inset-0 z-40 bg-white flex flex-col items-center justify-center space-y-8 text-xl font-bold md:hidden">
          <a href="#pass" onClick={() => setIsMenuOpen(false)}>여행 패스</a>
          <a href="#market" onClick={() => setIsMenuOpen(false)}>특산물 직거래</a>
          <a href="#funding" onClick={() => setIsMenuOpen(false)}>공동구매 펀딩</a>
          <a href="#business" onClick={() => setIsMenuOpen(false)}>수익 모델</a>
          <button className="bg-blue-600 text-white px-8 py-3 rounded-full">시작하기</button>
        </div>
      )}

      {/* Hero Section */}
      <section className="relative pt-32 pb-20 lg:pt-48 lg:pb-32 overflow-hidden">
        <div className="absolute top-0 right-0 -z-10 w-1/2 h-full bg-blue-50 rounded-bl-[100px]" />
        <div className="max-w-7xl mx-auto px-6 grid lg:grid-cols-2 gap-12 items-center">
          <div className="space-y-8">
            <div className="inline-flex items-center space-x-2 bg-blue-100 text-blue-700 px-4 py-1.5 rounded-full text-sm font-bold">
              <Sparkles className="w-4 h-4" />
              <span>AI가 만드는 지역 상생 플랫폼</span>
            </div>
            <h1 className="text-5xl lg:text-7xl font-extrabold text-gray-900 leading-[1.1]">
              지역과 여행을 잇다, <br />
              <span className="text-blue-600">이음 (IEUM)</span>
            </h1>
            <p className="text-xl text-gray-600 leading-relaxed max-w-xl">
              단 하나의 특별한 AI 여행 패스, 믿을 수 있는 특산물 직거래, 그리고 마음을 모으는 공동구매 크라우드 펀딩까지. 
              가치 있는 경험이 지역의 활력이 됩니다.
            </p>
            <div className="flex flex-col sm:flex-row space-y-4 sm:space-y-0 sm:space-x-4">
              <button className="bg-gray-900 text-white px-8 py-4 rounded-xl font-bold text-lg flex items-center justify-center hover:bg-black transition-all group">
                AI 여행 패스 만들기 <ChevronRight className="ml-2 group-hover:translate-x-1 transition-transform" />
              </button>
              <button className="border-2 border-gray-200 text-gray-700 px-8 py-4 rounded-xl font-bold text-lg hover:bg-gray-50 transition-all">
                진행중인 펀딩 보기
              </button>
            </div>
          </div>
          
          <div className="relative">
            {/* Mockup AI Interface */}
            <div className="bg-white rounded-3xl shadow-2xl p-6 border border-gray-100 relative z-10">
              <div className="flex items-center space-x-3 mb-6">
                <div className="w-10 h-10 bg-blue-600 rounded-full flex items-center justify-center">
                  <Sparkles className="text-white w-6 h-6" />
                </div>
                <div>
                  <h4 className="font-bold">이음 AI 어시스턴트</h4>
                  <p className="text-xs text-green-500">지금 바로 여정 설계 가능</p>
                </div>
              </div>
              <div className="space-y-4">
                <div className="bg-gray-100 p-4 rounded-2xl rounded-tl-none max-w-[85%]">
                  <p className="text-sm">"강릉으로 2박 3일 여행 갈 건데, 현지 교통패스랑 유명한 해산물 직거래 정보 좀 알려줘."</p>
                </div>
                <div className="bg-blue-50 p-4 rounded-2xl rounded-tr-none ml-auto max-w-[90%] border border-blue-100">
                  <p className="text-sm font-medium text-blue-800">
                    강릉 전용 '오션 블루 패스'를 구성해 드렸습니다. KTX 및 현지 버스 무제한 이용이 포함되어 있습니다. 
                    주문진항의 '김씨네 수산'에서 직거래 중인 오징어 판매 정보와, 현재 진행 중인 명란 젓갈 공동구매(펀딩) 링크도 함께 연결해 드릴까요?
                  </p>
                </div>
                <div className="flex space-x-2 pt-4">
                  <input type="text" placeholder="메시지를 입력하세요..." className="flex-1 bg-gray-50 border border-gray-200 rounded-lg px-4 py-2 text-sm focus:outline-none focus:ring-2 focus:ring-blue-500" />
                  <button className="bg-blue-600 text-white p-2 rounded-lg"><Zap className="w-5 h-5" /></button>
                </div>
              </div>
            </div>
            {/* Background Decoration */}
            <div className="absolute -bottom-10 -left-10 w-64 h-64 bg-blue-200/50 rounded-full blur-3xl -z-10" />
          </div>
        </div>
      </section>

      {/* Section 02: Core Features */}
      <section id="features" className="py-24 bg-gray-50">
        <div className="max-w-7xl mx-auto px-6">
          <div className="text-center max-w-3xl mx-auto mb-20">
            <h2 className="text-sm font-bold text-blue-600 tracking-widest uppercase mb-4">Core Services</h2>
            <h3 className="text-4xl font-bold mb-6">지역 발전을 위한 3대 핵심 서비스</h3>
            <p className="text-lg text-gray-600">
              '이음'은 단순한 여행 정보 제공을 넘어, 여행객과 지역 상인을 직접 연결하여 
              상생할 수 있는 탄탄한 인프라를 구축합니다.
            </p>
          </div>

          <div className="grid md:grid-cols-3 gap-10">
            {[
              { 
                icon: <Ticket className="w-10 h-10 text-blue-500" />, 
                title: "1. AI 맞춤 여행 패스 & 전용 코스", 
                desc: "사용자 취향과 지역 상황을 실시간으로 분석해, 교통·숙박·체험을 한 번에 해결하는 맞춤형 패스와 전용 코스를 제공합니다." 
              },
              { 
                icon: <Store className="w-10 h-10 text-orange-500" />, 
                title: "2. 특산물 판매자-구매자 직거래", 
                desc: "복잡한 유통망을 걷어내고 지역 판매자와 여행객을 직접 잇습니다. 신선한 특산물을 합리적인 가격에 거래하며 지역 상권을 살립니다." 
              },
              { 
                icon: <HeartHandshake className="w-10 h-10 text-green-500" />, 
                title: "3. 지역 특산물 공동구매 (펀딩)", 
                desc: "지역 농가 및 소상공인과 함께하는 크라우드 펀딩. 목표 인원 달성 시 파격적인 혜택을 제공하여 가치 소비를 유도합니다." 
              }
            ].map((item, i) => (
              <div key={i} className="bg-white p-10 rounded-3xl shadow-sm border border-gray-100 hover:shadow-xl transition-all h-full flex flex-col">
                <div className="mb-6">{item.icon}</div>
                <h4 className="text-xl font-bold mb-4">{item.title}</h4>
                <p className="text-gray-600 leading-relaxed flex-1">{item.desc}</p>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* View Details: Crowdfunding & Market */}
      <section className="py-24">
        <div className="max-w-7xl mx-auto px-6">
          <div className="flex flex-col lg:flex-row items-center gap-16">
            <div className="flex-1 space-y-8">
              <h3 className="text-4xl font-bold leading-tight">상생을 실현하는 <br/><span className="text-blue-600">스마트 로컬 생태계</span></h3>
              <p className="text-gray-600 text-lg">
                현지에서만 맛볼 수 있는 제철 특산물부터, 예약조차 어려운 숨겨진 장인들의 상품까지. 
                이음의 직거래망과 펀딩 시스템은 농가에는 안정적인 수익을, 구매자에겐 최상의 품질을 보장합니다.
              </p>
              
              <div className="space-y-6">
                <div className="flex items-start space-x-4">
                  <div className="mt-1 bg-green-100 p-2 rounded-xl text-green-600 flex-shrink-0">
                    <Timer className="w-6 h-6" />
                  </div>
                  <div>
                    <h5 className="font-bold text-lg">실시간 마감 임박 공동구매</h5>
                    <p className="text-gray-500 mt-1">강원 평창 고랭지 배추 100박스 한정 펀딩 (현재 85% 달성률). 직접 참여하여 농가를 응원하세요.</p>
                  </div>
                </div>
                <div className="flex items-start space-x-4">
                  <div className="mt-1 bg-orange-100 p-2 rounded-xl text-orange-600 flex-shrink-0">
                    <Store className="w-6 h-6" />
                  </div>
                  <div>
                    <h5 className="font-bold text-lg">인증된 현지 판매자 직거래</h5>
                    <p className="text-gray-500 mt-1">블록체인 기반의 이력 추적으로 믿을 수 있는 지역 판매자와 1:1 메시지를 나누며 직거래를 진행합니다.</p>
                  </div>
                </div>
              </div>
            </div>
            
            <div className="flex-1 w-full bg-gray-50 border border-gray-100 rounded-3xl p-8 relative overflow-hidden shadow-lg">
               <div className="absolute top-0 right-0 w-32 h-32 bg-blue-100 rounded-bl-full -z-0"></div>
               <h4 className="text-xl font-bold mb-6 relative z-10">🔥 주목받는 프로젝트</h4>
               
               {/* Funding Card */}
               <div className="bg-white rounded-2xl p-5 shadow-sm mb-4 relative z-10 border border-gray-100 hover:border-blue-300 transition-colors cursor-pointer">
                 <div className="flex justify-between items-center mb-3">
                   <span className="text-xs font-bold bg-blue-100 text-blue-700 px-2 py-1 rounded">크라우드 펀딩</span>
                   <span className="text-xs font-bold text-gray-500">2일 남음</span>
                 </div>
                 <h5 className="font-bold text-lg mb-1">[제주] 친환경 무농약 한라봉 직배송</h5>
                 <p className="text-sm text-gray-500 mb-4">제주 서귀포 김철수 농부님</p>
                 <div className="w-full bg-gray-100 rounded-full h-2 mb-2">
                   <div className="bg-blue-600 h-2 rounded-full" style={{ width: '88%' }}></div>
                 </div>
                 <div className="flex justify-between items-center text-sm font-bold">
                   <span className="text-blue-600">88% 달성</span>
                   <span>4,400,000원 모임</span>
                 </div>
               </div>

               {/* Market Card */}
               <div className="bg-white rounded-2xl p-5 shadow-sm relative z-10 border border-gray-100 hover:border-orange-300 transition-colors cursor-pointer">
                 <div className="flex justify-between items-center mb-3">
                   <span className="text-xs font-bold bg-orange-100 text-orange-700 px-2 py-1 rounded">직거래 매장</span>
                   <div className="flex items-center text-xs text-yellow-500 font-bold"><Sparkles className="w-3 h-3 mr-1"/> 평점 4.9</div>
                 </div>
                 <div className="flex items-center space-x-4">
                   <div className="w-16 h-16 bg-gray-200 rounded-xl overflow-hidden flex-shrink-0">
                      <img src="https://via.placeholder.com/100" alt="product mix" className="w-full h-full object-cover" />
                   </div>
                   <div>
                     <h5 className="font-bold text-md mb-1">통영 당일 조업 생굴 1kg</h5>
                     <p className="text-sm text-gray-500">통영바다수산 • 산지직송</p>
                     <p className="text-sm font-black mt-1">15,900원</p>
                   </div>
                 </div>
               </div>
            </div>
          </div>
        </div>
      </section>

      {/* Section 04: Revenue Model */}
      <section id="business" className="py-24 bg-blue-900 text-white overflow-hidden relative">
        <div className="absolute top-0 left-0 w-full h-full opacity-10">
          <div className="absolute top-10 left-10 w-96 h-96 border border-white rounded-full" />
          <div className="absolute -bottom-20 -right-20 w-[600px] h-[600px] border-4 border-white rounded-full" />
        </div>
        
        <div className="max-w-7xl mx-auto px-6 relative z-10 text-center">
          <h3 className="text-4xl font-bold mb-16">선순환 구조의 수익 모델</h3>
          <div className="grid md:grid-cols-3 gap-8">
            {[
              { 
                title: "맞춤형 여행 패스 마진", 
                list: ["지역 교통+식당+숙박 제휴 패스 판매", "기업(B2B) 대상 프리미엄 워케이션 패스"] 
              },
              { 
                title: "직거래 및 펀딩 수수료", 
                list: ["특산물 직거래 성사 시 소액 결제 수수료", "크라우드 펀딩 플랫폼 운영 수수료"] 
              },
              { 
                title: "로컬 데이터 솔루션(B2G)", 
                list: ["지자체 맞춤형 관광 데이터 및 컨설팅 제공", "지역 상권 활성화 솔루션 구축"] 
              }
            ].map((model, i) => (
              <div key={i} className="bg-white/10 backdrop-blur-lg border border-white/20 p-8 rounded-3xl text-left hover:bg-white/20 transition-all">
                <h4 className="text-xl font-bold mb-6 border-b border-white/20 pb-4">{model.title}</h4>
                <ul className="space-y-4">
                  {model.list.map((li, j) => (
                    <li key={j} className="flex items-start space-x-3 text-sm opacity-90 leading-relaxed">
                      <div className="w-1.5 h-1.5 bg-blue-400 rounded-full mt-1.5 flex-shrink-0" />
                      <span>{li}</span>
                    </li>
                  ))}
                </ul>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Expected Effects */}
      <section className="py-24">
        <div className="max-w-7xl mx-auto px-6">
          <div className="bg-gray-100 rounded-[50px] p-12 lg:p-20 flex flex-col lg:flex-row items-center gap-12">
            <div className="flex-1">
              <h3 className="text-4xl font-bold mb-8">가치 소비가 만드는 변화</h3>
              <div className="space-y-8">
                <div>
                  <span className="text-blue-600 font-bold text-lg">입체적 경제 성장</span>
                  <p className="text-gray-600 mt-2 text-lg italic font-medium">"유통 규격을 깬 직거래와 크라우드 펀딩으로 지역 농수산물 매출 극대화"</p>
                </div>
                <div>
                  <span className="text-orange-600 font-bold text-lg">신뢰 기반의 상생</span>
                  <p className="text-gray-600 mt-2 text-lg italic font-medium">"판매자와 구매자의 직접 연결로, 믿고 구매하는 로컬 소비 문화 정착"</p>
                </div>
              </div>
            </div>
            <div className="flex-1 grid grid-cols-2 gap-6">
              <div className="bg-white p-8 rounded-3xl text-center">
                <p className="text-4xl font-black text-blue-600">35<span className="text-2xl">%</span></p>
                <p className="text-sm font-bold text-gray-500 mt-2">유통 마진 절감</p>
              </div>
              <div className="bg-white p-8 rounded-3xl text-center mt-8 shadow-xl shadow-gray-200/50">
                <p className="text-4xl font-black text-orange-500">3.2<span className="text-2xl">x</span></p>
                <p className="text-sm font-bold text-gray-500 mt-2">지역 생산자 소득 증대</p>
              </div>
            </div>
          </div>
        </div>
      </section>

      {/* Footer */}
      <footer className="bg-white py-16 border-t border-gray-100">
        <div className="max-w-7xl mx-auto px-6 flex flex-col md:flex-row justify-between items-center space-y-8 md:space-y-0 text-center md:text-left">
          <div className="space-y-4">
            <div className="flex items-center justify-center md:justify-start space-x-2">
              <Train className="w-6 h-6 text-blue-600" />
              <span className="text-xl font-bold tracking-tighter">이음 (IEUM)</span>
            </div>
            <p className="text-gray-400 text-sm">생산관리 1조 | 반타오 연수진 이정재 진형준</p>
          </div>
          
          <div className="flex space-x-8 text-sm text-gray-500 font-medium">
            <a href="#" className="hover:text-blue-600">개인정보처리방침</a>
            <a href="#" className="hover:text-blue-600">이용약관</a>
            <a href="#" className="hover:text-blue-600">사업 제안</a>
            <a href="#" className="hover:text-blue-600">판매자/농가 등록</a>
          </div>
          
          <div className="text-sm text-gray-400">
            © 2025 IEUM Project. All rights reserved.
          </div>
        </div>
      </footer>
    </div>
  );
};

export default App;