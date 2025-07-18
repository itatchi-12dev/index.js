// Itatchi Bot – WhatsApp Bot Core // المتطلبات: Node.js, Express, Twilio (أو Meta WhatsApp API)

const express = require('express'); const bodyParser = require('body-parser'); const { MessagingResponse } = require('twilio').twiml;

const app = express(); app.use(bodyParser.urlencoded({ extended: false }));

app.post('/whatsapp', (req, res) => { const msg = req.body.Body.trim(); const twiml = new MessagingResponse(); const r = twiml.message();

switch (msg) { case '.أوامر': r.body(👋 مرحباً بك في Itatchi Bot\n\n🔹 الأوامر\n🔹 قيم البوت\n🔹 المطور); break;

case 'الأوامر':
  r.body(`📂 أقسام Itatchi Bot:\n

🌀 .الترفيه\n👥 .الجروب\n⬇️ .التحميل\n🕌 .الدين\n🏦 .التحويل\n👑 .المطور\n🎧 .الصوتيات\n🖼️ .الصور\n🖌️ .الايديت\n🎮 .الالعاب\n🤖 .AI\n🧰 .الادوات\n🏛️ .النقابات\n😆 .الرياكشنات\n🔍 .البحث\n🖼️ .اللوجوهات`); break;

case '.الترفيه':
  r.body(`🎭 أوامر الترفيه:\n.نكتة\n.حكمة\n.لو_خيروك\n.تحدي\n.صراحة\n.انمي_عشوائي`);
  break;

case '.الجروب':
  r.body(`👥 أوامر الجروب:\n.منشن\n.طرد @\n.كتم @\n.فك_كتم @\n.ترقية @\n.قوانين\n.عدد_الاعضاء`);
  break;

case '.التحميل':
  r.body(`⬇️ أوامر التحميل:\n.يوتيوب [رابط/كلمة]\n.فيديو [رابط]\n.صوت [رابط]\n.انستا [رابط]`);
  break;

case '.الدين':
  r.body(`🕌 أوامر الدين:\n.قرآن [سورة]\n.أذكار\n.حديث [كلمة]\n.دعاء\n.صلاة [مدينة]`);
  break;

case '.التحويل':
  r.body(`🏦 أوامر التحويل:\n.تحويل @ [مقدار]\n.رصيدي\n.بنك`);
  break;

case '.المطور':
  r.body(`👑 مطور البوت:\n📞 +212776026456 / +212654076271`);
  break;

case '.الصوتيات':
  r.body(`🎧 أوامر الصوتيات:\n.تكلم [نص]\n.تغيير_الصوت [نوع]\n.صوتيات`);
  break;

case '.الصور':
  r.body(`🖼️ أرسل: صورة [اسم] – وسأعطيك صورته.`);
  break;

case '.الايديت':
  r.body(`🖌️ أرسل: ايديت [اسم/موضوع] – وسأعطيك تصميم خاص.`);
  break;

case '.الالعاب':
  r.body(`🎮 ألعاب:\n.حجرة\n.تحداني\n.ذكاء\n.تخمين\n.رياضيات\n.اكس_او\n.كازينو\n.مخاطرة\n.تداول`);
  break;

case '.AI':
  r.body(`🤖 تحدث مع ذكاء صناعي:\n.ايتاتشي\n.ليفاي\n.غوجو\n.ريوك\n.أي شخصية – فقط اكتب اسمها`);
  break;

case '.الادوات':
  r.body(`🧰 أدوات:\n.طقس [مدينة]\n.وقت [مدينة]\n.ترجم [نص]\n.QR [نص]\n.زخرفة [نص]`);
  break;

case '.النقابات':
  r.body(`🏛️ نقابات البوت:\n.جروباتي – لعرض الجروبات التي فيها البوت.`);
  break;

case '.الرياكشنات':
  r.body(`😆 رياكشنات:\nاكتب: رياكشن [غضب/ضحك/حزن/...]`);
  break;

case '.البحث':
  r.body(`🔍 ابحث عن أي شيء:\n.بحث [شيء] – سأعطيك نتائج سريعة.`);
  break;

case '.اللوجوهات':
  r.body(`🖼️ لوجوهات PFP:\nاكتب: لوجو [اسم شخصية] – وسأعطيك صور بروفايل لها.`);
  break;

default:
  r.body("❓ لا أفهم هذا الأمر. أرسل .أوامر لعرض القائمة.");
  break;

}

res.writeHead(200, { 'Content-Type': 'text/xml' }); res.end(twiml.toString()); });

app.listen(3000, () => { console.log('✅ Itatchi Bot يعمل على http://localhost:3000'); });
