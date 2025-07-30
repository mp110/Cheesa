const roles = [
  { name: 'Trương Luc Nhương', chance: 0.3 },
  { name: 'Tô Tại Tại', chance: 0.2 },
  { name: 'Quan Phóng', chance: 0.5 },
    { name: 'Khương Giai', chance: 0.4 },
  { name: 'Cố Nhiên', chance: 0.5 },
];

function getRandomRole() {
  const r = Math.random();
  let sum = 0;
  for (const role of roles) {
    sum += role.chance;
    if (r < sum) {
      return role.name;
    }
  }
  // fallback, in case of rounding errors
  return roles[roles.length - 1].name;
}

// Discord bot example
const { Client, GatewayIntentBits } = require('discord.js');
const client = new Client({ intents: [GatewayIntentBits.Guilds, GatewayIntentBits.GuildMembers] });

client.on('messageCreate', async (message) => {
  if (message.content === '!blindbox') {
    const roleName = getRandomRole();
    const guildRole = message.guild.roles.cache.find(r => r.name === roleName);
    if (guildRole) {
      await message.member.roles.add(guildRole);
      message.reply(`Bạn vừa mở blind box F5 Giang Nghi và nhận được role: **${roleName}**!`);
    } else {
      message.reply(`Role "${roleName}" không tồn tại trong server.`);
    }
  }
});

client.login('YOUR_DISCORD_BOT_TOKEN');
