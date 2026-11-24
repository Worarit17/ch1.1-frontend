
<template>
  <q-page padding>
    <div class="text-h4 q-mb-md">
      Version Control + Docker Demo (Quasar)
    </div>

    <q-card class="q-mb-md">
      <q-card-section>
        <div class="text-h6">Git Workflow (ตัวอย่างขั้นตอนทำงาน)</div>
        <q-list bordered separator class="q-mt-sm">
          <q-item v-for="(step, index) in gitSteps" :key="index">
            <q-item-section avatar>
              <q-badge>{{ index + 1 }}</q-badge>
            </q-item-section>
            <q-item-section>
              <q-item-label>{{ step.title }}</q-item-label>
              <q-item-label caption>{{ step.detail }}</q-item-label>
            </q-item-section>
          </q-item>
        </q-list>
      </q-card-section>
    </q-card>

    <q-card class="q-mb-md">
      <q-card-section>
        <div class="text-h6">Docker Concepts (สรุปสั้น ๆ)</div>
        <q-list bordered separator class="q-mt-sm">
          <q-item v-for="item in dockerItems" :key="item.title">
            <q-item-section>
              <q-item-label>{{ item.title }}</q-item-label>
              <q-item-label caption>{{ item.detail }}</q-item-label>
            </q-item-section>
          </q-item>
        </q-list>
      </q-card-section>
    </q-card>

    <q-card class="q-mt-md">
      <q-card-section class="bg-primary text-white">
        <div class="text-h6">
          <q-icon name="terminal" class="q-mr-sm" />
          Docker Quick Reference
        </div>
        <div class="text-caption">
          คำสั่งพื้นฐาน Docker และ Docker Compose
        </div>
      </q-card-section>

      <q-card-section>
        <div class="row q-col-gutter-md">
          <div
            v-for="item in dockerCommands"
            :key="item.command"
            class="col-12 col-sm-6"
          >
            <q-card bordered flat class="full-height">
              <q-card-section>
                <div class="text-subtitle1 text-weight-bold">
                  {{ item.title }}
                </div>
                <q-badge color="blue" class="q-mb-sm">
                  {{ item.type }}
                </q-badge>
                <div class="bg-grey-10 text-white q-pa-sm rounded-borders">
                  <code>{{ item.command }}</code>
                </div>
                <div class="text-body2 q-mt-sm">
                  {{ item.description }}
                </div>
              </q-card-section>
            </q-card>
          </div>
        </div>
      </q-card-section>
    </q-card>
  </q-page>
</template>

<script setup>
const gitSteps = [
  {
    title: 'แก้โค้ด Quasar ใน src/',
    detail: 'เพิ่มหน้า / component ใหม่ เช่น IndexPage.vue, Layout ต่าง ๆ',
  },
  {
    title: 'ตรวจสอบสถานะไฟล์',
    detail: 'ใช้ git status ดูว่าไฟล์ไหนเปลี่ยนแปลงบ้าง',
  },
  {
    title: 'เพิ่มไฟล์เข้า staging',
    detail: 'ใช้ git add frontend/src/pages/IndexPage.vue',
  },
  {
    title: 'สร้าง commit พร้อมข้อความแบบ Conventional Commits',
    detail: 'เช่น feat: add Git workflow demo page',
  },
  {
    title: 'push ขึ้น GitHub',
    detail: 'ใช้ git push -u origin feature/quasar-demo แล้วเปิด Pull Request',
  },
]

const dockerItems = [
  {
    title: 'Image',
    detail: 'แพ็กเกจที่มีไฟล์และการตั้งค่าที่ใช้สร้าง container เช่น image ที่รวม Quasar SPA กับ Nginx',
  },
  {
    title: 'Container',
    detail: 'อินสแตนซ์ที่สร้างจาก image เช่น container ที่รัน Nginx เพื่อเสิร์ฟไฟล์ Quasar',
  },
  {
    title: 'Volume',
    detail: 'เก็บข้อมูลให้คงอยู่แยกจากวงจรชีวิตของ container เช่น ไฟล์อัปโหลดของ backend',
  },
  {
    title: 'Network',
    detail: 'ให้บริการใน Docker ติดต่อกันได้ เช่น Nginx ส่งต่อคำขอไปยัง Express',
  },
]

const dockerCommands = [
  {
    title: 'แสดง Container',
    type: 'Docker',
    command: 'docker ps',
    description: 'ใช้แสดงรายการ Container ที่กำลังทำงานอยู่',
  },
  {
    title: 'แสดง Images',
    type: 'Docker',
    command: 'docker images',
    description: 'ใช้ตรวจสอบ Images ที่ดาวน์โหลดหรือสร้างไว้ในเครื่อง',
  },
  {
    title: 'ดู Logs',
    type: 'Docker',
    command: 'docker logs <container>',
    description: 'ใช้ตรวจสอบ Log เพื่อค้นหาข้อผิดพลาดของ Container',
  },
  {
    title: 'เริ่มต้น Services',
    type: 'Docker Compose',
    command: 'docker compose up -d',
    description: 'ใช้เริ่มต้น Services ทั้งหมดใน Background',
  },
  {
    title: 'ตรวจสอบ Services',
    type: 'Docker Compose',
    command: 'docker compose ps',
    description: 'ใช้ตรวจสอบสถานะ Services ที่กำหนดไว้ใน Compose',
  },
  {
    title: 'ดู Compose Logs',
    type: 'Docker Compose',
    command: 'docker compose logs',
    description: 'ใช้ดู Log ของ Services ทั้งหมดใน Docker Compose',
  },
]
</script>
