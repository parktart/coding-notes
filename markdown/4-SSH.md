# About SSH

SSH (Secure Shell) is a network communication protocol that enables two computers to communicate.

When you generate an SSH key pair using SSH keygen, you create both a private key and a public key.

The private key is a secret key that is generated on your computer. It remains on your device and should be kept securely, as it should never be shared with anyone. The private key is used to decrypt messages that are encrypted with the corresponding public key.

The public key, on the other hand, is intended to be shared with others. You can distribute your public key to other entities or servers with whom you want to communicate securely using SSH. The public key can be freely shared without compromising the security of your communication.

When someone receives your public key, they do not have the corresponding private key. The private key always remains with the key pair generator, which is you in this case. The public key is derived from the private key through a mathematical process, but it is computationally infeasible to reverse-engineer the private key from the public key.

The entity or server that receives your public key can use it to encrypt messages or data that they want to send to you securely. Once the data is encrypted with your public key, only your private key can decrypt it. Therefore, even though the other entity may have a copy of your public key, they cannot decrypt the messages they send to you because they do not possess your private key.

So, after you provide GitHub with a public key you generated on your local machine, you'll be able to clone/pull repos from GitHub onto your local machine.

Also, when you attempt to push things to GitHub, your local machine will request to authenticate an SSH connection so that it may push things. GitHub will respond with a message, ecrypted using your public key, that your machine will then unlock using your private key and send back to GitHub. This proves you have a the corresponding private key and you are who you say you are. The SSH connection is authenticated and you are free to push files/etc.