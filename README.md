# Fashion Lookbook Collage

A Codex skill that turns one seller-supplied apparel reference into a vertical, multi-view lookbook collage. It preserves the visible product while creating three complementary lifestyle views, a central coherent outfit cutout, palette chips, and restrained editorial details.

中文版说明见下方。

## What it makes

- A fixed four-panel 2 × 2 lookbook layout
- The source photo unchanged in the top-left panel
- Three generated companion views of the same person in the same outfit
- A central headless outfit cutout that keeps dependent layers together
- Small product-derived palette chips and understated scrapbook details

## Install

In Codex, ask:

```text
Use $skill-installer to install https://github.com/mizzyhuang/fashion-lookbook-collage
```

## Use

Upload a clear apparel or outfit image, then write:

```text
Use $fashion-lookbook-collage to turn this image into a fixed four-panel vertical fashion lookbook collage.
```

For a more specific request:

```text
Use $fashion-lookbook-collage. Keep the supplied image unchanged in the top-left panel; generate the other three panels as the same outfit in standing, seated, and walking poses. Keep the full upper look together in the central cutout.
```

## Notes

- Use a clear source image that reveals the garment, accessories, and silhouette.
- The skill treats the source image as product evidence: it should not redesign, recolour, or invent SKU details.
- Do not add images you do not own or have permission to publish to this repository.

---

## 中文说明

这个 Codex skill 会把一张卖家提供的服饰或穿搭参考图，转为固定四坑位的纵向穿搭灵感拼贴：左上保留原图，另外三格生成同一人物、同一套服装的不同视角；中央则保留完整、合理的穿搭抠图。

### 安装

在 Codex 中输入：

```text
使用 $skill-installer 安装 https://github.com/mizzyhuang/fashion-lookbook-collage
```

### 调用

上传一张清晰穿搭图后输入：

```text
使用 $fashion-lookbook-collage，把这张图做成固定四坑位的纵向穿搭灵感拼贴。
```

### 规则亮点

- 左上始终是未改动的原图。
- 右上、左下、右下是相同人物与相同服装的新增视角。
- 有外套和内搭的情况，中央抠图保留完整上身组合，不把内搭机械拆成单独商品。
- 服装颜色、版型、图案、五金、鞋包和可见配饰以原图为准。

## License

MIT. See [LICENSE](LICENSE).
