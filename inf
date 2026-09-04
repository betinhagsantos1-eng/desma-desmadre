const {
  Client,
  GatewayIntentBits,
  EmbedBuilder,
  Events
} = require('discord.js');

const client = new Client({
  intents: [
    GatewayIntentBits.Guilds,
    GatewayIntentBits.GuildMembers
  ]
});

client.once(Events.ClientReady, (readyClient) => {
  console.log(`💜 DÉSMA está online como ${readyClient.user.tag}!`);
});

client.on(Events.GuildMemberAdd, async (member) => {
  try {
    const channelId = process.env.ID_DO_CANAL_DE_BOAS_VINDAS;

    if (!channelId) {
      console.log('❌ ID do canal de boas-vindas não configurado.');
      return;
    }

    const channel = await member.guild.channels.fetch(channelId);

    if (!channel || !channel.isTextBased()) {
      console.log('❌ Canal de boas-vindas não encontrado.');
      return;
    }

    const embed = new EmbedBuilder()
      .setTitle('👑💜 ¡BIENVENID@ AL DESMADRE! 💜👑')
      .setDescription(
        `¡Ey, <@${member.id}>! 😎\n\n` +
        `Soy **DÉSMA**, tu anfitrión oficial por aquí. 👑\n\n` +
        `Llegaste hasta aquí, así que oficialmente ya eres parte del caos. 😂💜\n\n` +
        `Aquí somos familia, fiesta, locura y mucho DESMADRE.\n` +
        `Date una vuelta por los canales, conoce las reglas y ponte cómod@.\n\n` +
        `💜 **NUEVA FAMILIA • NUEVAS LOCURAS • MISMO DESMADRE** 💜\n\n` +
        `👑 ¡Que comience el DESMADRE! 👑`
      )
      .setThumbnail(member.user.displayAvatarURL({ dynamic: true }))
      .setFooter({
        text: 'DÉSMA • Familia DESMADRE 👑'
      })
      .setTimestamp();

    await channel.send({
      content: `💜 <@${member.id}>`,
      embeds: [embed]
    });

    console.log(`✅ Boas-vindas enviadas para ${member.user.tag}`);

  } catch (error) {
    console.error('❌ Erro ao enviar boas-vindas:', error);
  }
});

client.login(process.env.DISCORD_TOKEN);
