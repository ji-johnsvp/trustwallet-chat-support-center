# trustwallet-chat-support-center
import React, { useState } from 'react';
import { Send } from 'lucide-react';

const ChatInterface = () => {
  const [message, setMessage] = useState('');
  const [messages, setMessages] = useState([
    {
      id: 1,
      sender: 'user',
      text: "Hello, I'm having issues accessing my wallet.",
      time: '10:30 AM'
    },
    {
      id: 2,
      sender: 'agent',
      text: "Hello! Welcome to Trust Wallet Support. I'm Emily, your Support Specialist. Please provide the details of your issue and I'll be happy to help you.",
      time: '10:31 AM',
      agentName: 'Emily - Support Specialist'
    }
  ]);

  const handleSendMessage = () => {
    if (message.trim()) {
      const newMessage = {
        id: messages.length + 1,
        sender: 'user',
        text: message,
        time: new Date().toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' })
      };
      
      setMessages([...messages, newMessage]);
      setMessage('');
    }
  };
  const handleKeyPress = (e: React.KeyboardEvent) => {
    if (e.key === 'Enter') {
      handleSendMessage();
    }
  };

  return (
    <div className="bg-white rounded-lg shadow-lg border border-gray-200 h-96 flex flex-col">
      {/* Chat Header */}
      <div className="bg-blue-600 text-white p-4 rounded-t-lg flex items-center">
        <div className="w-3 h-3 bg-green-400 rounded-full mr-3"></div>
        <div>
          <h3 className="font-semibold">Trust Wallet Support</h3>
          <p className="text-sm text-blue-100">Online - Avg. response time: 2 min</p>
        </div>
      </div>

      {/* Messages Area */}
      <div className="flex-1 p-4 overflow-y-auto space-y-4">
        {messages.map((msg) => (
          <div
            key={msg.id}
            className={`flex ${msg.sender === 'user' ? 'justify-end' : 'justify-start'}`}
          >
            <div className={`max-w-xs lg:max-w-md px-4 py-2 rounded-lg ${
              msg.sender === 'user' 
                ? 'bg-blue-600 text-white' 
                : 'bg-gray-100 text-gray-800'
            }`}>
              {msg.sender === 'agent' && (
                <p className="text-xs text-blue-600 font-semibold mb-1">{msg.agentName}</p>
              )}
              <p className="text-sm">{msg.text}</p>
              <p className={`text-xs mt-1 ${
                msg.sender === 'user' ? 'text-blue-100' : 'text-gray-500'
              }`}>
                {msg.time}
              </p>
            </div>
          </div>
        ))}
      </div>
      {/* Input Area */}
      <div className="p-4 border-t border-gray-200">
        <div className="flex space-x-3">
          <input
            type="text"
            value={message}
            onChange={(e) => setMessage(e.target.value)}
            onKeyPress={handleKeyPress}
            placeholder="Type your message..."
            className="flex-1 px-4 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent outline-none"
          />
          <button
            onClick={handleSendMessage}
            className="bg-blue-600 hover:bg-blue-700 text-white p-2 rounded-lg transition-colors"
          >
            <Send size={20} />
          </button>
        </div>
      </div>
    </div>
  );
};

export default FloatingChatButton;
import React from 'react';

const Footer = () => {
  return (
    <footer className="bg-gray-900 text-white py-12">
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div className="grid grid-cols-1 md:grid-cols-3 gap-8">
          {/* Company Info */}
          <div>
            <div className="flex items-center mb-4">
              <div className="w-8 h-8 bg-blue-600 rounded-lg flex items-center justify-center">
                <span className="text-white font-bold">T</span>
              </div>
              <span className="ml-2 text-lg font-semibold">Trust Wallet</span>
            </div>
            <p className="text-gray-400 text-sm">
              Your trusted companion for secure cryptocurrency storage and DeFi access.
            </p>
          </div>
{/* Social Media */}
          <div>
            <h4 className="text-lg font-semibold mb-4">Follow Us</h4>
            <div className="flex space-x-4">
              <a href="#" className="text-gray-400 hover:text-white transition-colors">
                <span className="sr-only">Twitter</span>
                <div className="w-8 h-8 bg-gray-700 rounded-lg flex items-center justify-center hover:bg-blue-600 transition-colors">
                  𝕏
                </div>
              </a>
              <a href="#" className="text-gray-400 hover:text-white transition-colors">
                <span className="sr-only">Telegram</span>
                <div className="w-8 h-8 bg-gray-700 rounded-lg flex items-center justify-center hover:bg-blue-500 transition-colors">
                  ✈
                </div>
              </a>
              <a href="#" className="text-gray-400 hover:text-white transition-colors">
                <span className="sr-only">Discord</span>
                <div className="w-8 h-8 bg-gray-700 rounded-lg flex items-center justify-center hover:bg-indigo-600 transition-colors">
                  💬
                </div>
              </a>
            </div>
          </div>
        </div>

        <div className="mt-8 pt-8 border-t border-gray-800 text-center">
          <p className="text-gray-400 text-sm">
            © 2024 Trust Wallet. All rights reserved.
          </p>
        </div>
      </div>
    </footer>
  );
};

export default Footer;
import React from 'react';
import { MessageSquare } from 'lucide-react';

const Header = () => {
  const navItems = ['Home', 'Support Center', 'FAQs', 'Security Tips', 'Contact Us'];

  return (
    <header className="bg-white shadow-sm border-b border-gray-200 sticky top-0 z-50">
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div className="flex justify-between items-center h-16">
          {/* Logo */}
          <div className="flex items-center">
            <div className="w-10 h-10 bg-blue-600 rounded-lg flex items-center justify-center">
              <span className="text-white font-bold text-lg">T</span>
            </div>
            <span className="ml-3 text-xl font-semibold text-gray-900">Trust Wallet Support</span>
          </div>

          {/* Navigation */}
          <nav className="hidden md:flex space-x-8">
            {navItems.map((item, index) => (
              <a
                key={index}
                href="#"
                className="text-gray-700 hover:text-blue-600 px-3 py-2 text-sm font-medium transition-colors"
              >
                {item}
              </a>
            ))}
          </nav>
          import React from 'react';

const HelpTopics = () => {
  const topics = [
    { title: 'Recover Wallet', icon: '🔐', color: 'bg-blue-50 border-blue-200' },
    { title: 'Transaction Issues', icon: '💸', color: 'bg-yellow-50 border-yellow-200' },
    { title: 'Security Guidelines', icon: '🛡️', color: 'bg-green-50 border-green-200' },
    { title: 'How to Connect to DApps', icon: '🔗', color: 'bg-purple-50 border-purple-200' }
  ];

  return (
    <div className="bg-white rounded-lg shadow-lg p-6 border border-gray-200">
      <h3 className="text-lg font-semibold text-gray-900 mb-4">Common Help Topics</h3>
      <div className="space-y-3">
        {topics.map((topic, index) => (
          <button
            key={index}
            className={`w-full text-left p-4 rounded-lg border-2 transition-all hover:shadow-md ${topic.color} hover:scale-105`}
          >
            <div className="flex items-center space-x-3">
              <span className="text-2xl">{topic.icon}</span>
              <span className="font-medium text-gray-800">{topic.title}</span>
            </div>
          </button>
        ))}
      </div>
    </div>
  );
};

export default HelpTopics;
import React from 'react';

const HeroSection = () => {
  return (
    <section className="bg-gradient-to-br from-blue-50 to-indigo-100 py-16">
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
        <h1 className="text-4xl md:text-5xl font-bold text-gray-900 mb-4">
          Welcome to Trust Wallet Support Center
        </h1>
        <p className="text-xl text-gray-600 mb-8 max-w-2xl mx-auto">
          Need help? Our Support Team is available 24/7 to assist you with any questions or issues.
        </p>
        
        {/* Security Badges */}
        <div className="flex justify-center items-center space-x-8 mb-8">
          <div className="flex items-center space-x-2 bg-white px-4 py-2 rounded-full shadow-sm">
            <div className="w-3 h-3 bg-green-500 rounded-full"></div>
            <span className="text-sm font-medium text-gray-700">SSL Secured</span>
          </div>
          <div className="flex items-center space-x-2 bg-white px-4 py-2 rounded-full shadow-sm">
            <div className="w-3 h-3 bg-blue-500 rounded-full"></div>
            <span className="text-sm font-medium text-gray-700">Official Trust Wallet Help</span>
          </div>
        </div>
      </div>
    </section>
  );
};

export default HeroSection;
import React from 'react';

const SecurityNotice = () => {
  return (
    <div className="bg-amber-50 border-l-4 border-amber-400 p-4 rounded-r-lg mb-8">
      <div className="flex">
        <div className="flex-shrink-0">
          <span className="text-2xl">⚠️</span>
        </div>
        <div className="ml-3">
          <p className="text-sm text-amber-800">
            <strong>Important Security Notice:</strong> Trust Wallet Support will never ask for your Secret Recovery Phrase or Private Keys. 
            Keep this information secure and never share it with anyone.
          </p>
        </div>
      </div>
    </div>
  );
};

export default SecurityNotice;
// Update this page (the content is just a fallback if you fail to update the page)

const Index = () => {
  return (
    <div className="min-h-screen flex items-center justify-center bg-background">
      <div className="text-center">
        <h1 className="text-4xl font-bold mb-4">Welcome to Your Blank App</h1>
        <p className="text-xl text-muted-foreground">Start building your amazing project here!</p>
      </div>
      import React from 'react';
import Header from '../components/Header';
import HeroSection from '../components/HeroSection';
import ChatInterface from '../components/ChatInterface';
import HelpTopics from '../components/HelpTopics';
import SecurityNotice from '../components/SecurityNotice';
import FloatingChatButton from '../components/FloatingChatButton';
import Footer from '../components/Footer';

const Index = () => {
  return (
    <div className="min-h-screen bg-gray-50">
      <Header />
      <HeroSection />
      
      {/* Main Content */}
      <main className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12">
        <SecurityNotice />
        
        <div className="grid grid-cols-1 lg:grid-cols-3 gap-8">
          {/* Chat Interface */}
          <div className="lg:col-span-2">
            <ChatInterface />
          </div>
          {/* Help Topics Sidebar */}
          <div className="lg:col-span-1">
            <HelpTopics />
          </div>
        </div>
      </main>
      
      <Footer />
      <FloatingChatButton />
    </div>
  );
};

export default Index;
<!-- Begin of Chaport Live Chat code -->
<script type="text/javascript">
(function(w,d,v3){
w.chaportConfig = {
appId : '6862633c6cabe22f04688afb'
};

if(w.chaport)return;v3=w.chaport={};v3._q=[];v3._l={};v3.q=function(){v3._q.push(arguments)};v3.on=function(e,fn){if(!v3._l[e])v3._l[e]=[];v3._l[e].push(fn)};var s=d.createElement('script');s.type='text/javascript';s.async=true;s.src='https://app.chaport.com/javascripts/insert.js';var ss=d.getElementsByTagName('script')[0];ss.parentNode.insertBefore(s,ss)})(window, document);
</script>
<!-- End of Chaport Live Chat code -->
