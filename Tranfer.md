# Tranfer.md

สรุปการคุยและการตัดสินใจทั้งหมดของโปรเจกต์ SecondBrain จนถึงตอนนี้

วันที่สรุป: 2026-06-27

## 1. Repository และ Git

เริ่มจากสร้าง repository สำหรับ SecondBrain และเชื่อมกับ GitHub:

- Repository path: `D:\ProjectAP\SecondBrain`
- Remote: `https://github.com/apiwatapply-svg/SecondBrain.git`
- Default branch: `main`
- Commit แรก: `first commit`

มีการตั้งค่า git identity เฉพาะ repo นี้เป็น:

- `user.name`: `apiwatapply-svg`
- `user.email`: `apiwatapply-svg@users.noreply.github.com`

สถานะล่าสุดที่เคย push:

- `ab3d456 Add React POS agent rules`
- `d02862d Restructure workspace around knowledge vault`
- `74ddcc5 Ingest Karpathy LLM Wiki source`
- `c19eb58 Require YouTube channel metadata on ingest`
- `6f315d5 Build LLM wiki architecture`
- `86e5331 first commit`

## 2. แนวคิดหลักของ SecondBrain

เราตั้งระบบตามแนวคิด LLM Wiki ของ Andrej Karpathy:

- Raw sources เป็นหลักฐานดิบและ source of truth
- Wiki เป็นชั้นความรู้ที่ LLM สังเคราะห์และดูแล
- `AGENTS.md` เป็น schema/กติกาให้ AI ทำงานอย่างมีวินัย
- `index.md` เป็นแผนที่เนื้อหา
- `log.md` เป็นประวัติการ ingest/query/lint/schema change

แหล่งอ้างอิงหลัก:

- `https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f`

## 3. โครงสร้าง Workspace ปัจจุบัน

เราปรับโครงสร้างให้ `SecondBrain` เป็น workspace root และแยก vault จริงไว้ใน `knowledge/`:

```text
D:\ProjectAP\SecondBrain\
  AGENTS.md
  README.md
  .gitignore
  Tranfer.md

  knowledge\
    .obsidian\
    AGENTS.md
    README.md
    index.md
    log.md
    raw\
    wiki\
    templates\
    operations\

  projects\
    README.md
    react-pos\
      AGENTS.md
      front-end\
      back-end\

  examples\
    second-brain-web-AGENTS.example.md
```

ให้เปิด Obsidian ที่:

```text
D:\ProjectAP\SecondBrain\knowledge
```

ให้เปิด Codex/AI workspace ที่:

```text
D:\ProjectAP\SecondBrain
```

## 4. AGENTS.md แต่ละระดับ

### Root AGENTS.md

ตำแหน่ง:

```text
D:\ProjectAP\SecondBrain\AGENTS.md
```

หน้าที่:

- เป็น workspace router
- บอก AI ว่า task ไหนควรไป `knowledge/`
- task ไหนควรไป `projects/<project-name>/`
- register โปรเจกต์ที่มีอยู่จริง
- บอก boundary ว่าอย่าเอา app source code ไปไว้ใน vault และอย่าเอา markdown vault ไปปนใน project code

### Knowledge AGENTS.md

ตำแหน่ง:

```text
D:\ProjectAP\SecondBrain\knowledge\AGENTS.md
```

ไฟล์นี้คือ AGENTS เดิมของ LLM Wiki ถูกย้ายมาเฉย ๆ ไม่ได้เปลี่ยนเนื้อหาเมื่อย้ายจาก root มา `knowledge/`.

หน้าที่:

- กำหนดกติกา LLM Wiki
- อธิบาย `raw/`, `wiki/`, `templates/`, `operations/`
- กำหนด workflow ingest/query/lint/promote
- กำหนด naming/frontmatter/evidence rules
- มีกฎ YouTube source rules

### Project AGENTS.md ของ React POS

ตำแหน่ง:

```text
D:\ProjectAP\SecondBrain\projects\react-pos\AGENTS.md
```

หน้าที่:

- บอก AI ว่าโปรเจกต์นี้คือ React POS
- frontend อยู่ที่ `front-end/`
- backend อยู่ที่ `back-end/`
- ถ้าต้องใช้ความรู้ ให้อ่านจาก `D:\ProjectAP\SecondBrain\knowledge`

Stack ที่ระบุแล้ว:

- Frontend: React
- Backend: Node.js
- Database: Microsoft SQL Server (MSSQL)
- ORM: Prisma 6

## 5. LLM Wiki Architecture ที่สร้างไว้

ใน `knowledge/` มีโครงหลัก:

```text
knowledge\
  raw\
    inbox\
    sources\
    assets\

  wiki\
    maps\
    areas\
    projects\
    topics\
    concepts\
    entities\
    people\
    sources\
    syntheses\
    questions\

  templates\
  operations\
  index.md
  log.md
  AGENTS.md
```

ไฟล์สำคัญ:

- `knowledge/index.md` - content map
- `knowledge/log.md` - chronological activity log
- `knowledge/operations/ingest-source.md` - วิธี ingest
- `knowledge/operations/query-wiki.md` - วิธีถาม wiki
- `knowledge/operations/lint-wiki.md` - วิธีตรวจสุขภาพ wiki
- `knowledge/operations/promote-chat-answer.md` - วิธีบันทึกคำตอบจาก chat เป็น wiki page

## 6. Source ที่ ingest แล้ว

มีการ ingest Karpathy LLM Wiki gist แล้ว:

Raw source:

```text
knowledge/raw/sources/2026-06-23-karpathy-llm-wiki.md
```

Source brief:

```text
knowledge/wiki/sources/karpathy-llm-wiki-gist.md
```

และเพิ่ม alias page เพื่อ resolve author wikilink จาก Obsidian Web Clipper:

```text
knowledge/wiki/people/262588213843476.md
```

## 7. YouTube Web Clipper Rule

เราเพิ่มกฎว่าเวลา ingest YouTube video ที่ save จาก Obsidian Web Clipper หรือเป็น YouTube URL:

- ต้องดึง channel name จาก YouTube เอง
- ต้องใส่ `channel_name` ใน frontmatter
- ถ้ามี ให้ใส่ `channel_url` และ `video_id`
- ใช้ `source_type: youtube-video`
- ถ้าดึงไม่ได้ ให้ใส่ `channel_name: needs-review` และบันทึกใน source brief/log

Template ที่สร้างไว้:

```text
knowledge/templates/youtube-video-source.md
```

## 8. วิธีใช้งานประจำวัน

### เก็บ source

1. ใช้ Obsidian Web Clipper หรือวางไฟล์เอง
2. วาง source ใหม่ใน `knowledge/raw/inbox/` ถ้าเป็น source ของ vault
3. สั่ง AI ว่า `ingest`

### Ingest

เมื่อสั่ง ingest, AI ควร:

1. อ่าน `knowledge/AGENTS.md`
2. อ่าน `knowledge/operations/ingest-source.md`
3. ย้าย accepted source เข้า `knowledge/raw/sources/`
4. สร้าง/อัปเดต source brief ใน `knowledge/wiki/sources/`
5. อัปเดต topic/concept/entity/person/synthesis ที่เกี่ยวข้อง
6. อัปเดต `knowledge/index.md`
7. เพิ่ม entry ใน `knowledge/log.md`

### Query

เมื่อถามจาก wiki, AI ควร:

1. อ่าน `knowledge/index.md`
2. อ่าน wiki pages ที่เกี่ยวข้อง
3. อ่าน raw source เฉพาะเมื่อจำเป็น
4. ตอบพร้อม wikilinks/citations
5. ถ้าคำตอบใช้ซ้ำได้ ให้ promote เป็น page ใน `wiki/questions/` หรือ `wiki/syntheses/`

### Lint

ทุก ๆ 5-10 sources ควรสั่ง:

```text
lint wiki
```

เพื่อตรวจ:

- broken links
- orphan pages
- duplicate concepts
- stale pages
- source briefs ที่ไม่เชื่อมกับ topic/concept
- contradictions

## 9. หลักการเรื่องโปรเจกต์หลายตัว

ตัดสินใจแล้วว่าไม่ควรเอา web app/source code ไปปนใน Obsidian vault โดยตรง

ใช้หลัก:

```text
SecondBrain = workspace root
knowledge = Obsidian vault / LLM Wiki
projects = code projects
```

ข้อดี:

- Obsidian ไม่ต้อง scan `node_modules`, `.next`, build output
- AI ยังเห็นทั้ง knowledge และ code เพราะเปิด workspace ที่ root
- แต่ละ project มี AGENTS.md แยกได้
- สิทธิการเข้าถึงชัดกว่า

## 10. React POS Project

โปรเจกต์ที่ register แล้ว:

```text
D:\ProjectAP\SecondBrain\projects\react-pos
```

โครงปัจจุบัน:

```text
projects/react-pos/
  AGENTS.md
  front-end/
  back-end/
```

กติกาที่ใส่ไว้:

- งาน UI/frontend ไป `front-end/`
- งาน API/database/backend ไป `back-end/`
- Prisma schema/migrations/database access อยู่ `back-end/`
- ถ้าต้องใช้ความรู้ให้อ่าน `knowledge/`
- ถ้ายังไม่มี package manager files ห้ามเดาเงียบ ๆ ให้ถามหรือทำตาม stack ที่ user ระบุ

## 11. Example AGENTS.md

มีตัวอย่าง AGENTS สำหรับ future web project:

```text
examples/second-brain-web-AGENTS.example.md
```

ไฟล์นี้เป็นตัวอย่างเท่านั้น ไม่ใช่ project จริง

## 12. สิ่งที่ต้องระวังต่อไป

### raw/ untracked ที่ root

ตอนล่าสุดมี `raw/` untracked อยู่ที่ root:

```text
D:\ProjectAP\SecondBrain\raw
```

ดูเหมือนเป็น React documentation ที่ยังไม่ได้ ingest หรือจัดเข้าที่

อย่า commit ปนกับงานอื่นโดยไม่ตั้งใจ

ควรตัดสินใจภายหลังว่าจะ:

1. ย้ายเข้า `knowledge/raw/inbox/` แล้ว ingest
2. ลบถ้าไม่ต้องการ
3. เก็บเป็น source batch สำหรับ React docs

### Workspace path สะกดผิดในบาง context

บาง environment context เคยระบุ path เป็น:

```text
D:\ProjectAP\SecoundBrain
```

แต่ path จริงที่ใช้คือ:

```text
D:\ProjectAP\SecondBrain
```

ถ้า command เปิดไม่ได้ ให้เช็ก path นี้ก่อน

## 13. แนวทางต่อไปที่น่าทำ

1. ตัดสินใจว่าจะ ingest `raw/` root ที่เป็น React docs หรือไม่
2. ถ้าจะทำ React POS ต่อ ให้เริ่มเลือก package manager และ scaffold frontend/backend
3. สร้าง `.env.example` ของแต่ละฝั่งเมื่อเริ่มเขียนโค้ดจริง
4. ถ้ามี business rule ของ POS ให้เก็บใน `knowledge/wiki/projects/` หรือ source brief ก่อน แล้วให้ project code อ้างอิงจาก knowledge
5. ถ้าสร้าง backend จริง ให้ระบุ Prisma 6 + MSSQL connection strategy ให้ชัดใน backend docs
