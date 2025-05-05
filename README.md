# yesilarkadas
import discord
from discord.ext import commands
import random
import os
intents = discord.Intents.default()
intents.message_content = True
bot = commands.Bot(command_prefix='$', intents=intents)


bilgiler = [
    "🌍Bir pet şişe doğada 450 yıl kalır🌍"
    "🌲Bir ton kağıt 17 tane ağacın hayatını kurtarır🌲"
    "🌊Bir ton plastik 2.000 litre petrol demektir🌊"
]
@bot.event
async def on_ready():
    print(f'{bot.user} olarak giriş yaptık')
@bot.command()
async def hello(ctx):
    await ctx.send(f'Merhaba! Ben {bot.user}, bir çevreci Discord botuyum;)')
@bot.command()
async def bilgi(ctx):
    bilgi = random.choice(bilgiler)
    await ctx.send(bilgi)
@bot.command()
async def mem(ctx):
    liste=os.listdir("yesilarkadas")
    resim=random.choice(liste)
    with open(f'yesilarkadas/{resim}', 'rb') as f:
        # Dönüştürülen Discord kütüphane dosyasını bu değişkende saklayalım!
        picture = discord.File(f)
   # Daha sonra bu dosyayı bir parametre olarak gönderebiliriz!
    await ctx.send(file=picture)
bot.run("MTM2NjQ3NTM0MjgyMjI0NDM3Mg.GWjokj.2PtML1dfZnAlQAU7dHrTSEAL3kZA0xer3ZwxYw")

