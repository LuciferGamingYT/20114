const Discord = require("discord.js"); // We use Discord.JS
const bot = new Discord.Client();

const prefix = "!"; // Prefix untuk Bot
const ownerID = ""; // ID Owner Bot

bot.on("message", message => {
  // Deklarasi :v
  let args = message.content.slice(prefix.length).trim.split(" ");
  let cmd = args.shift().toLowerCase();

  // Tempat Pembatalan Process :v
  if (message.author.bot) return; // Bot tidak akan respon jika yang menggunakannya adalah sesama Bot
  if (!message.content.startsWith(prefix)) return; // Bot tidak akan respon jika tidak dijalankan menggunakan Prefix
  if (!message.guild) return; // Bot tidak akan respon jika dijalankan melalui DM

  // Command Handler
  try {
    let commandFile = require(`./commands`);
  } catch (e) {
    // Ini akan nge-catch segala error, kecuali perintah tidak tersedia
    console.log(e.stack);
  }
});

bot.on("ready", () => console.log("Bot Sudah Dihidupkan!"));

bot.login(process.env.BOT_TOKEN);
