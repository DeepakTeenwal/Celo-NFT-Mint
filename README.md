# 🎯 Celo Quiz NFT - Farcaster Mini App

A Farcaster Mini App where users answer quiz questions about Celo blockchain and mint NFTs based on their score!

## 🌟 Features

- **Score-Based NFT Minting**: 
  - 1 correct answer = 1 NFT
  - 2 correct answers = 2 NFTs
  - 3 correct answers = 3 NFTs (All!)
- **Farcaster Integration**: Native wallet support and user context
- **One-by-one Quiz**: Interactive quiz with progress tracking
- **Multi-Wallet Support**: Works with Farcaster wallet or external wallets (MetaMask, etc.)
- **Celo Blockchain**: Built on Celo mainnet

## 🚀 Live Demo

**App URL**: https://celo-nft-mint.vercel.app

**Contract Address**: `0x6a31E0ac5184A1263812abd764E8813A79AEE8cF` (Celo Mainnet)

## 📁 Repository Structure

```
celo-nft-mint/
├── index.html           # Main app
├── farcaster.json       # Farcaster manifest
├── icon.png             # App icon (200x200px)
├── preview.png          # Preview image (1200x630px)
├── splash.png           # Splash screen (1200x1200px) - optional
├── vercel.json          # Vercel config - optional
└── README.md            # This file
```

## 🛠️ Setup Instructions

### Step 1: Generate Account Association

1. Go to: https://miniapps.farcaster.xyz/tools/signature-generator
2. Enter:
   - **Domain**: `celo-nft-mint.vercel.app`
   - **Your Farcaster FID**: (Your FID number)
3. Copy the generated `header`, `payload`, and `signature`
4. Update `farcaster.json` with these values

### Step 2: Create Images

Use the image generator tool (image-templates.html) or create manually:

**icon.png** - 200x200px
- Your app icon for Farcaster

**preview.png** - 1200x630px
- Preview image when sharing

**splash.png** - 1200x1200px (optional)
- Loading screen

### Step 3: Verify Contract Setup

Your contract should have token URIs added via `addTokenURI()` function. Check that:
- At least 3 token URIs are registered in the contract
- URIs point to valid IPFS metadata
- Contract is properly configured

You can check this by calling `getAllTokenURIs()` on the contract.

### Step 4: Deploy to Vercel

1. Push all files to GitHub
2. Import repository to Vercel
3. Deploy (automatic)
4. Your app is live at: https://celo-nft-mint.vercel.app

### Step 5: Test Your App

1. Enable Developer Mode in Farcaster:
   - Visit: https://farcaster.xyz/~/settings/developer-tools
   - Toggle "Developer Mode" ON

2. Test the app:
   - Open Farcaster app
   - Go to Developer section
   - Enter: `https://celo-nft-mint.vercel.app`
   - Click "Open"

3. Test functionality:
   - Answer quiz questions
   - Check wallet connection
   - Try minting NFTs (on testnet first!)

## 📋 Files Checklist

Before going live:

- [ ] `index.html` - Production ready (no changes needed!)
- [ ] `farcaster.json` - Account association generated with YOUR FID
- [ ] `icon.png` - Created and uploaded
- [ ] `preview.png` - Created and uploaded
- [ ] `splash.png` - Created and uploaded (optional)
- [ ] `vercel.json` - Added for CORS headers (optional)
- [ ] Contract verified: `0x6a31E0ac5184A1263812abd764E8813A79AEE8cF`
- [ ] Contract has token URIs configured (check `getAllTokenURIs()`)
- [ ] Tested in Farcaster Developer Mode

## 🎮 How It Works

1. **User Opens App**: Via Farcaster or direct link
2. **Takes Quiz**: Answers 3 questions about Celo
3. **Gets Score**: System counts correct answers
4. **Claims NFTs**: 
   - Connects wallet (Farcaster or external)
   - Switches to Celo network
   - Calls `claimNFTs(correctAnswers)` - single transaction!
   - Contract automatically mints 1-3 NFTs based on score
5. **Receives NFTs**: Check wallet on Celo Explorer

## 🔧 Smart Contract

**Address**: `0x6a31E0ac5184A1263812abd764E8813A79AEE8cF`

**Network**: Celo Mainnet (Chain ID: 42220)

**Explorer**: https://explorer.celo.org/address/0x6a31E0ac5184A1263812abd764E8813A79AEE8cF

**Main Function**: `claimNFTs(uint8 correctAnswers)`
- Users can only claim once (checked via `hasClaimed` mapping)
- Contract automatically assigns NFT URIs based on score
- Emits `NFTsClaimed` event with token IDs

**Features**:
- ✅ One-time claim per address
- ✅ Single transaction for all NFTs
- ✅ Score-based NFT distribution
- ✅ Event emission for tracking

## 🌐 Celo Network Details

- **Chain ID**: 42220 (0xa4ec)
- **RPC URL**: https://forno.celo.org
- **Block Explorer**: https://explorer.celo.org
- **Native Token**: CELO

## 📱 Farcaster Features Used

- ✅ SDK Integration (`@farcaster/miniapp-sdk`)
- ✅ User Context (FID, username, avatar)
- ✅ Wallet Provider (`sdk.wallet.getEthereumProvider()`)
- ✅ Add to Favorites (`sdk.actions.addMiniApp()`)
- ✅ Ready Signal (`sdk.actions.ready()`)
- 🔜 Notifications (coming soon)

## 🎨 Customization

### Change Quiz Questions

Edit in `index.html`:

```javascript
const questions = [
  {
    q: "Your question here?",
    options: ["Option A", "Option B", "Option C", "Option D"],
    answer: "Option B"
  },
  // Add more questions...
];
```

### Change Colors

Update CSS gradients in `index.html`:

```css
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
```

### Change Contract

Update contract address:

```javascript
const CONTRACT_ADDRESS = "0xYourNewContractAddress";
```

## 🐛 Troubleshooting

### "Failed to load manifest"
- Ensure `farcaster.json` is at root
- Check JSON is valid
- Verify domain matches deployment

### "Invalid signature"
- Regenerate account association
- Use correct FID
- Match domain exactly

### Wallet not connecting
- Check you're on production domain
- Clear browser cache
- Try different wallet

### NFTs not claiming
- Check if you've already claimed (one claim per address)
- Verify contract address is correct
- Check wallet has CELO for gas
- Ensure contract has token URIs configured
- Verify contract is on Celo mainnet
- Check contract has minting enabled

## 📚 Resources

- **Farcaster Mini Apps Docs**: https://miniapps.farcaster.xyz/docs
- **Celo Docs**: https://docs.celo.org
- **Ethers.js Docs**: https://docs.ethers.org
- **IPFS Docs**: https://docs.ipfs.tech

## 🤝 Contributing

Feel free to fork and customize this app for your own use!

## 📄 License

MIT License - feel free to use this code for your projects!

## 🎉 Next Steps

1. ✅ Generate account association signature
2. ✅ Create and upload images
3. ✅ Update NFT URIs with real IPFS hashes
4. ✅ Test in Farcaster Developer Mode
5. ✅ Share your Mini App with the community!

---

**Built with ❤️ on Celo blockchain**

Need help? Join the Farcaster or Celo Discord communities!
