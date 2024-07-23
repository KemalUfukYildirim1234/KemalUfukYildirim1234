import discord
import random

intents = discord.Intents.default()
intents.message_content = True
client = discord.Client(intents=intents)

@client.event
async def on_ready():
    print(f'{client.user} olarak giriş yaptık')

@client.event
async def on_message(message):
    if message.author == client.user:
        return
    
    if message.content.startswith('$hello'):
        await message.channel.send(f'Merhaba {client.user}! ben bir botum!')

    elif message.content.startswith('$heh'):
        if len(message.content) > 4:
            try:
                count_heh = int(message.content[4:])
            except ValueError:
                count_heh = 5
        else:
            count_heh = 5
        await message.channel.send("he" * count_heh)

    elif message.content.startswith('$geri dönüştürülebilen atıklar'):
        await message.channel.send("Kağıt, Metal, Cam gibi atıklar")

    elif message.content.startswith('$geri dönüştürülemeyen atıklar'):
        await message.channel.send("Karbon kağıdı, Atık yiyecekler gibi atıklar")

    elif message.content.startswith('$rastgele sayı at'):
        random_number = random.randint(1, 100)
        await message.channel.send(f'Rastgele sayı: {random_number}')

    elif message.content.startswith('$iklim değişikliği'):
        await message.channel.send("İklim değişikliği, uzun vadede hava durumu ve sıcaklık gibi iklim modellerindeki değişikliklere denir.")

    elif message.content.startswith('$küresel ısınma'):
        await message.channel.send("Küresel ısınma, atmosfere salınan sera gazları nedeniyle Dünya'nın ortalama yüzey sıcaklığının artmasıdır.")

    elif message.content.startswith('$karbon ayak izi'):
        await message.channel.send("Karbon ayak izi, bir kişinin, organizasyonun, etkinliğin veya ürünün neden olduğu toplam sera gazı emisyonlarının ölçüsüdür.")

    elif message.content.startswith('$yenilenebilir enerji'):
        await message.channel.send("Yenilenebilir enerji, doğal olarak yenilenebilen ve tükenmeyen enerji kaynaklarından elde edilen enerjidir. Güneş, rüzgar, hidroelektrik ve biyokütle enerjileri bunlara örnektir.")

    elif message.content.startswith('$su tasarrufu'):
        await message.channel.send("Su tasarrufu, suyun verimli kullanımı ve israfın önlenmesi için yapılan uygulamaları içerir. Muslukları kapatmak, suyu tekrar kullanmak gibi yöntemler su tasarrufuna örnektir.")
    
    elif message.content.startswith("$çevre ile ilgili bir resim at"):
        with open("sustainable-living-environmentalist-hand-holding-green-earth.jpg","rb") as f:
            resim = discord.File(f)
        await message.channel.send(file=resim)
    
client.run("token")
