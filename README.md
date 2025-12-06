import React, { useState, useEffect } from 'react';
import { Sparkles, Zap, Infinity, ArrowRight } from 'lucide-react';

export default function NovaAILanding() {
  const [mousePosition, setMousePosition] = useState({ x: 0, y: 0 });
  const [isVisible, setIsVisible] = useState(false);

  useEffect(() => {
    setIsVisible(true);
    const handleMouseMove = (e) => {
      setMousePosition({ x: e.clientX, y: e.clientY });
    };
    window.addEventListener('mousemove', handleMouseMove);
    return () => window.removeEventListener('mousemove', handleMouseMove);
  }, []);

  const benefits = [
    {
      icon: <Zap className="w-8 h-8" />,
      title: "Lightning Speed",
      description: "Generate professional-grade images in seconds, no more waiting"
    },
    {
      icon: <Sparkles className="w-8 h-8" />,
      title: "Infinite Creativity",
      description: "From idea to visual, AI makes every creative vision possible"
    },
    {
      icon: <Infinity className="w-8 h-8" />,
      title: "Endless Possibilities",
      description: "No design skills needed, everyone becomes an artist"
    }
  ];

  return (
    <div className="relative min-h-screen bg-black text-white overflow-hidden">
      <style>{`
        @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Inter:wght@300;400;500&display=swap');
        
        * {
          margin: 0;
          padding: 0;
          box-sizing: border-box;
        }

        body {
          font-family: 'Inter', sans-serif;
        }

        .gradient-text {
          background: linear-gradient(135deg, #00f5ff 0%, #0099ff 50%, #00ccff 100%);
          -webkit-background-clip: text;
          background-clip: text;
          -webkit-text-fill-color: transparent;
        }

        .glow {
          box-shadow: 0 0 20px rgba(0, 245, 255, 0.3),
                      0 0 40px rgba(0, 245, 255, 0.2),
                      0 0 60px rgba(0, 245, 255, 0.1);
        }

        .grid-background {
          background-image: 
            linear-gradient(rgba(0, 245, 255, 0.05) 1px, transparent 1px),
            linear-gradient(90deg, rgba(0, 245, 255, 0.05) 1px, transparent 1px);
          background-size: 50px 50px;
          animation: gridMove 20s linear infinite;
        }

        @keyframes gridMove {
          0% { background-position: 0 0; }
          100% { background-position: 50px 50px; }
        }

        @keyframes fadeInUp {
          from {
            opacity: 0;
            transform: translateY(30px);
          }
          to {
            opacity: 1;
            transform: translateY(0);
          }
        }

        @keyframes float {
          0%, 100% { transform: translateY(0px); }
          50% { transform: translateY(-20px); }
        }

        @keyframes pulse {
          0%, 100% { opacity: 0.4; }
          50% { opacity: 0.8; }
        }

        .fade-in-up {
          animation: fadeInUp 0.8s ease-out forwards;
        }

        .float {
          animation: float 6s ease-in-out infinite;
        }

        .hover-lift {
          transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .hover-lift:hover {
          transform: translateY(-8px) scale(1.02);
        }

        .btn-glow {
          position: relative;
          overflow: hidden;
        }

        .btn-glow::before {
          content: '';
          position: absolute;
          top: 0;
          left: -100%;
          width: 100%;
          height: 100%;
          background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.3), transparent);
          transition: left 0.5s;
        }

        .btn-glow:hover::before {
          left: 100%;
        }

        .particle {
          position: absolute;
          width: 2px;
          height: 2px;
          background: #00f5ff;
          border-radius: 50%;
          animation: pulse 3s ease-in-out infinite;
        }
      `}</style>

      {/* Animated Grid Background */}
      <div className="grid-background absolute inset-0 opacity-30"></div>

      {/* Floating Particles */}
      {[...Array(20)].map((_, i) => (
        <div
          key={i}
          className="particle"
          style={{
            left: `${Math.random() * 100}%`,
            top: `${Math.random() * 100}%`,
            animationDelay: `${Math.random() * 3}s`,
            opacity: Math.random() * 0.5 + 0.2
          }}
        />
      ))}

      {/* Mouse Glow Effect */}
      <div
        className="absolute w-96 h-96 rounded-full pointer-events-none"
        style={{
          background: 'radial-gradient(circle, rgba(0, 245, 255, 0.15) 0%, transparent 70%)',
          left: mousePosition.x - 192,
          top: mousePosition.y - 192,
          transition: 'all 0.3s ease-out'
        }}
      />

      {/* Content Container */}
      <div className="relative z-10 max-w-7xl mx-auto px-6 py-20">
        {/* Header */}
        <header className={`text-center mb-32 ${isVisible ? 'fade-in-up' : 'opacity-0'}`}>
          <div className="inline-block mb-6 float">
            <div className="text-6xl md:text-8xl font-black tracking-tighter" style={{ fontFamily: "'Orbitron', sans-serif" }}>
              <span className="gradient-text">NOVA</span>
              <span className="text-white ml-4">AI</span>
            </div>
          </div>
          
          <p className="text-xl md:text-2xl text-gray-400 font-light max-w-2xl mx-auto leading-relaxed mb-12"
             style={{ animationDelay: '0.2s' }}>
            Next-Generation AI Image Creation Platform
            <br />
            <span className="text-sm text-gray-500 mt-2 block">Turn imagination into reality, in an instant</span>
          </p>

          <button className="btn-glow glow px-10 py-4 bg-gradient-to-r from-cyan-500 to-blue-500 rounded-full font-semibold text-lg hover:shadow-2xl transform transition-all duration-300 hover:scale-105 flex items-center gap-3 mx-auto group"
                  style={{ animationDelay: '0.4s' }}>
            Start Creating
            <ArrowRight className="w-5 h-5 group-hover:translate-x-1 transition-transform" />
          </button>
        </header>

        {/* Benefits Section */}
        <section className={`${isVisible ? 'fade-in-up' : 'opacity-0'}`} style={{ animationDelay: '0.6s' }}>
          <h2 className="text-4xl md:text-5xl font-bold text-center mb-4" style={{ fontFamily: "'Orbitron', sans-serif" }}>
            Why Choose <span className="gradient-text">AI Image Generation</span>
          </h2>
          <p className="text-center text-gray-500 mb-16 text-lg">Revolutionize your creative workflow</p>

          <div className="grid md:grid-cols-3 gap-8">
            {benefits.map((benefit, index) => (
              <div
                key={index}
                className="hover-lift bg-gradient-to-br from-gray-900 to-black border border-gray-800 rounded-2xl p-8 relative overflow-hidden group"
                style={{ animationDelay: `${0.8 + index * 0.2}s` }}
              >
                {/* Card Glow Effect */}
                <div className="absolute inset-0 bg-gradient-to-br from-cyan-500/0 to-blue-500/0 group-hover:from-cyan-500/10 group-hover:to-blue-500/10 transition-all duration-500 rounded-2xl"></div>
                
                <div className="relative z-10">
                  <div className="mb-6 text-cyan-400 inline-block p-4 bg-cyan-500/10 rounded-xl">
                    {benefit.icon}
                  </div>
                  
                  <h3 className="text-2xl font-bold mb-4 text-white" style={{ fontFamily: "'Orbitron', sans-serif" }}>
                    {benefit.title}
                  </h3>
                  
                  <p className="text-gray-400 leading-relaxed">
                    {benefit.description}
                  </p>
                </div>

                {/* Corner Accent */}
                <div className="absolute top-0 right-0 w-20 h-20 bg-gradient-to-br from-cyan-500/20 to-transparent rounded-bl-full"></div>
              </div>
            ))}
          </div>
        </section>

        {/* CTA Section */}
        <section className={`mt-32 text-center ${isVisible ? 'fade-in-up' : 'opacity-0'}`} style={{ animationDelay: '1.4s' }}>
          <div className="relative inline-block">
            <div className="absolute inset-0 bg-gradient-to-r from-cyan-500 to-blue-500 blur-3xl opacity-30 animate-pulse"></div>
            <div className="relative bg-gradient-to-br from-gray-900 to-black border border-cyan-500/30 rounded-3xl p-12 md:p-16">
              <h2 className="text-4xl md:text-5xl font-black mb-6" style={{ fontFamily: "'Orbitron', sans-serif" }}>
                Ready to Get Started?
              </h2>
              <p className="text-gray-400 text-lg mb-8 max-w-xl mx-auto">
                Join millions of creators and unleash your infinite creativity with AI
              </p>
              <button className="btn-glow px-12 py-5 bg-white text-black rounded-full font-bold text-lg hover:shadow-2xl transform transition-all duration-300 hover:scale-105">
                Try It Now
              </button>
            </div>
          </div>
        </section>

        {/* Footer */}
        <footer className="mt-32 text-center text-gray-600 text-sm">
          <div className="h-px bg-gradient-to-r from-transparent via-gray-800 to-transparent mb-8"></div>
          <p>© 2024 Nova AI. Powered by imagination.</p>
        </footer>
      </div>
    </div>
  );
}
