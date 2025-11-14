const mineflayer = require('mineflayer')

function startBot() {
    const bot = mineflayer.createBot({
        host: "SUNUCU_ADRESI",   // <-- Buraya sunucu adresini yaz
        port: 25565,
        username: "AFKBot"       // Botun ismi
    });

    bot.on('login', () => {
        console.log("Bot sunucuya bağlandı!")
    });

    // Her 5 dakikada bir mesaj gönderir
    setInterval(() => {
        bot.chat("AFK ama burdayım :)")
    }, 5 * 60 * 1000);

    // Kafasını sağ-sol oynatma (anti-AFK)
    setInterval(() => {
        bot.look(bot.entity.yaw + 0.5, bot.entity.pitch, true);
    }, 20 * 1000);
}

startBot();
