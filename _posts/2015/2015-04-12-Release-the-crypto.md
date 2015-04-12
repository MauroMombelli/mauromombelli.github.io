---
layout: default
title: IDEA to make cryptovalues a real thing. 
excerpt: We need to create a easy way to make and accept fast and small payment in first person
thumbnail: /images/2015/doge.png
---

# {{title}}

{{excerpt}}


we need to create a easy way to make and accept payment.
when you buy online, or a expansive thing, it is OK to way many minutes to have one or more confirmation.
but think about buying a coffee or a dinner; over a couple of seconds is an overkill.
also inputting address and value is a pain.
and finally we don't want to take out our private key, and connect to unknown network.
Obviously we don't wanna use physical coin, so we need an alternative.

so here my idea.

* we need fast confirmation for small value.
we don't want to end up like mtgov, but for a coffee one block confirmation is fine.
that exclude bitcoin and litecoin, and the only coin with big market and community is DogeCoin.
that is an obligated choose in my opinion, but fell free to point other coin.
* we need something safe to use, like a prepaid; a dedicated wallet is the obvious decision.
* we need a secure and offline way to sign transaction; this can be done if the wallet hystory is known
* you need to know the transaction from where you will take the coin, and the private and public key used to create and sign that address.
you will also need the receiving address, the price and the suggested tip


this is known by a little and not expansive machine, with some wireless data exchange like zibee,Bluetooth,nfc,or even WiFi or barcode

How it works

* The HW wallet will show the value and ask for confirmation
* if user confirm, based on off-linestored data the transaction is created
* the remaining coin will put again on the same HW wallet address
* the transaction signed is sent to shop, probably with the same system used to get the information.
* the shop is connected to the network, so inject the transaction to pool and so the miner may elaborate it
* if the transaction is accepted, a light turn yellow, if not red. (also a rollback request is sent to the HW wallet)
when the transaction's block is mined, the light turn green, a confimation message goest to the wallet.
* end of payment.


Please note; this is possible because the wallet know the history of the address is using to pay;
when a transaction is accepted, the next will have a different sign(by bitcoin protocol);
this is why we need to rollback failed transition and confirm accepet.
Maybe is a nice idea to let the user be able to override one confirmation/reject, so he can recovery from a bad state without the need of a PC;
if the transaction is maliciously failed, as you rollback your last transaction,
the wallet will be out of sync and will produce invalid sing.
this also mean the wallet have to remember all its transaction to correctly sign the next;

but please note that the buyer-seller protocol is easy and does not require trust.
the worse is that your wallet will be unusable until you sync it (we hope from a secure source!)


## what the seller need?

a little machine connected to internet, and the only setup is the receiving address.
a little numpad will be used to input the value.

a normal PC may be used, if communication technology with walled are fine.
another secured PC to store the wallet. or whatever you preferr

## what the buyer need?

this HW wallet. it will also need to set up it;
at first boot or on a special HW pin, it will generate an adress. 
then you'll put some coin on it with a transaction; 
then you need to synch the history of the wallet, probably sending a stanard JSON rappresentation of its transaction.
as the number of input transaction will be limited (probably 1, but aldo depends on HW capabilities), if you want to load more coin
the idea is to empty the actual address, and then make a new transaction on it, and finally sync again.
the last input transaction will be used as source of coin.

obviously that sync may be done to resync an unsynchronized wallet because erroneus transaction or similar.