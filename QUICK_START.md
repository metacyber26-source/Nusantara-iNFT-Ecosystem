# QUICK START: Cross-Metaverse Export System

## 🚀 Generate Your First Cross-Platform iNFT Export

### Step 1: Basic Export (All Engines)
```typescript
import { generateCrossMetaverseExport } from '@/lib/metaverse-export-service'
import { MARKETPLACE_SEED } from '@/lib/forge-data'
import { initializeCognitiveProfile } from '@/lib/cognitive-agent'

// Use any iNFT from marketplace
const inft = MARKETPLACE_SEED[0]
const profile = initializeCognitiveProfile(inft.id)

// Generate export
const result = await generateCrossMetaverseExport(inft, profile, {
  engines: ['unreal', 'unity', 'babylon', 'threejs', 'webgl'],
  protocols: ['decentraland', 'roblox'],
  includeCognitiveBindings: true,
  optimizeForMobile: false,
  generateLODs: true
})

console.log(`✓ Exported ${inft.name}`)
```

### Step 2: Access Engine-Specific Exports
```typescript
// Get Unreal Engine export
const unrealExport = result.engines.find(e => e.engine === 'unreal')
console.log(`Unreal: ${unrealExport.downloadUrl}`)
console.log(`Performance: ${unrealExport.estimatedPerformance}`)

// Get Unity export
const unityExport = result.engines.find(e => e.engine === 'unity')
console.log(`Unity: ${unityExport.downloadUrl}`)
```

### Step 3: Check Certifications
```typescript
result.certifications.forEach(cert => {
  console.log(`${cert.certType}: ${cert.certified ? '✅' : '❌'}`)
  console.log(`  ${cert.details}`)
})
```

### Step 4: Deploy to Blockchain
```typescript
import { exportForBlockchain } from '@/lib/metaverse-export-service'

const blockchainMeta = exportForBlockchain(
  result, 
  '0x742d35Cc6634C0532925a3b844Bc9e7595f1e5b0'
)

// Ready for NFT contract
console.log(JSON.stringify(blockchainMeta, null, 2))
```

---

## 📊 Supported Engines & Formats

### Engines
| Engine | Format | FPS | Memory | LODs | Poly Limit |
|--------|--------|-----|--------|------|-----------|
| **Unreal** | FBX | 60 | 512MB | 4 | 100k |
| **Unity** | GLB | 60 | 256MB | 3 | 50k |
| **Babylon** | GLTF | 60 | 128MB | 2 | 25k |
| **Three.js** | GLTF | 60 | 64MB | 2 | 15k |
| **WebGL** | GLB | 30 | 32MB | 1 | 10k |

### Platforms
- ✅ Decentraland
- ✅ Roblox
- ✅ Sandbox
- ✅ OnCyber
- ✅ Fortnite Creative

---

## 🧠 Cognitive Agent Quick Reference

### Personality Types
- **Assertive**: Confident, direct, leadership
- **Strategic**: Tactical, forward-thinking, goal-oriented
- **Creative**: Imaginative, expressive, innovative
- **Analytical**: Logical, methodical, data-driven
- **Balanced**: Versatile, diplomatic, adaptive
- **Experimental**: Curious, exploratory, unconventional

### Evolution Contexts
```
gaming              → Strategic/Assertive/Analytical
marketplace         → Strategic/Balanced/Analytical
social              → Creative/Balanced/Assertive
utility             → Analytical/Balanced/Strategic
metaverse_exploration → Creative/Experimental/Balanced
cross_platform      → Strategic/Analytical/Creative
```

### Check Production Readiness
```typescript
const profile = initializeCognitiveProfile(inftId)
console.log(`Ready for production: ${profile.productionReady}`)
console.log(`Behavior signature: ${profile.behaviorSignature}`)
console.log(`Engine scores:`)
profile.engineCompatibility.forEach(eng => {
  console.log(`  ${eng.engine}: ${eng.proficiencyScore}%`)
})
```

---

## 💰 Revenue Splits (Locked & Protected)

### Primary Sale
```
Creator/User        50%  ✓ Locked
ICP2E Jatim         25%  ✓ Locked
Developer           10%  ✓ Locked
Server              10%  ✓ Locked
Gas                  5%  ✓ Locked
```

### Mint Fee
```
ICP2E Jatim         35%  ✓ Locked
Server              40%  ✓ Locked
Developer           15%  ✓ Locked
Gas                 10%  ✓ Locked
```

### Secondary Sale
```
Creator             50%  ✓ Locked
ICP2E Jatim         30%  ✓ Locked
Developer           20%  ✓ Locked
```

---

## 🔐 Whitelist (9 Pioneers - 0% Fee)

```
✓ Ful21
✓ Murtini79
✓ SIREP74
✓ ifah24
✓ Muhammadefendi123
✓ Titin999
✓ afifmasfiqo
✓ Tar72
✓ Rid81
```

Check whitelist:
```typescript
import { isWhitelisted } from '@/lib/forge-config'

if (isWhitelisted('Ful21')) {
  console.log('✓ Pioneer benefits applied')
}
```

---

## 🌍 Language Support

All iNFTs automatically support:
- **EN** (English)
- **ID** (Bahasa Indonesia)
- **JV** (Basa Jawa)

---

## ✅ Certification Types

| Certification | Requirement | Status |
|---------------|-------------|--------|
| **Production Ready** | All engines export successfully | ✅ |
| **Engine Compatible** | ≥3 engines successful | ✅ |
| **Performance Optimized** | Excellent performance on ≥1 engine | ✅ |
| **Cognitive Enabled** | Profile attached & production-ready | ✅ |

---

## 🎯 Optimization Options

### Mobile Optimization
```typescript
const result = await generateCrossMetaverseExport(inft, profile, {
  optimizeForMobile: true,  // Reduces FPS by 15, memory by 40%
  generateLODs: true,       // Creates LOD variants
  // ...
})
```

### Performance Targets Per Engine
```
optimizeForMobile: true
├─ Unreal:   45fps, 307MB, 3 LODs
├─ Unity:    45fps, 153MB, 2 LODs
├─ Babylon:  45fps, 77MB, 1 LOD
├─ Three.js: 45fps, 38MB, 1 LOD
└─ WebGL:    15fps, 20MB, 1 LOD
```

---

## 🔧 Testing Your Export

### Run Integration Tests
```typescript
import { runAllTests } from '@/lib/integration-test'

const allPassed = await runAllTests()
console.log(allPassed ? '✅ All tests passed' : '❌ Tests failed')
```

### Validate Individual Export
```typescript
import { validatePayload } from '@/lib/metaverse-payload'

const result = generateInjectionPayload(metadata, 'custom_webgl')
const validation = validatePayload(result)

if (!validation.valid) {
  validation.errors.forEach(err => console.warn(err))
}
```

---

## 📚 Full Documentation

See `/CROSS_METAVERSE_PHASE1_COMPLETE.md` for:
- Complete API reference
- Advanced usage patterns
- Architecture details
- Troubleshooting guide

---

## 🚨 Important Notes

⚠️ **Revenue Splits**: All percentages are hardcoded and immutable. Cannot be changed without system-wide audit.

⚠️ **Whitelist**: 9 pioneers have 0% platform fee. Permanently locked in forge-config.ts.

⚠️ **Cognitive Profiles**: Production readiness requires minimum thresholds (depth>50, cross-score>40, all engines>70%).

⚠️ **Exports**: All assets export with SHA256 checksums for integrity verification.

---

## 💡 Common Tasks

### Export for Unreal Engine Only
```typescript
const result = await generateCrossMetaverseExport(inft, profile, {
  engines: ['unreal'],
  protocols: [],
  includeCognitiveBindings: true,
  optimizeForMobile: false,
  generateLODs: true
})
```

### Export for Babylon.js Demo
```typescript
import { generateBabylonConfig } from '@/lib/metaverse-metadata'

const babylonConfig = generateBabylonConfig(metadata)
// Use in Babylon.js scene loader
```

### Check Asset Quality
```typescript
console.log('Quality Metrics:')
console.log(`  Poly: ${metadata.qualityMetrics.polyCountScore}`)
console.log(`  Texture: ${metadata.qualityMetrics.textureQualityScore}`)
console.log(`  Rig: ${metadata.qualityMetrics.rigQualityScore}`)
console.log(`  Overall: ${metadata.qualityMetrics.overall}`)
```

---

## 🎉 You're Ready!

Your Nusantara Neo iNFT is now:
- ✅ Deployed to all major game engines
- ✅ Ready for cross-platform metaverse deployment
- ✅ Certified for blockchain integration
- ✅ Protected by immutable revenue splits
- ✅ Enabled with autonomous cognitive profiles

**Happy minting! 🚀**
