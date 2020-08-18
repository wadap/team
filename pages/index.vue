<template>
  <div>
    <div class="columns is-one-third-widescreen">
      <div class="column">
        <b-field label="名前">
          <b-input v-model="names" type="textarea"></b-input>
        </b-field>
      </div>
      <div class="column">
        <div class="field">
          <b-field label="チーム数">
            <b-select v-model="teamCount" placeholder="チーム数">
              <option v-for="num in 5" :key="num">
                {{ num }}
              </option>
            </b-select>
          </b-field>
        </div>
      </div>
    </div>
    <div class="buttons">
      <b-button type="is-primary" expanded @click="exec">チーム分け</b-button>
    </div>
    <div class="columns is-one-third-widescreen">
      <div v-for="ct in parseInt(teamCount)" :key="ct" class="column">
        <b-field label="名前">
          <b-input v-model="teams[ct - 1]" type="textarea" disabled></b-input>
        </b-field>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Home',
  components: {},
  data() {
    return {
      names: '',
      teams: [],
      teamCount: 2,
    }
  },
  methods: {
    exec() {
      const nameList = this.names.split('\n')
      const memberNum = Math.floor(nameList.length / this.teamCount)

      const eachSlice = (arr, n = 2) => {
        const dup = [...arr]
        const result = []
        let length = dup.length

        while (length > 0) {
          result.push(dup.splice(0, n))
          length = dup.length
        }

        return result
      }

      const result = eachSlice(nameList, memberNum)
      const orgMem = result.filter((e) => e.length === memberNum)
      const addMem = result.filter((e) => e.length !== memberNum).shift()

      if (addMem) {
        for (let i = 0; i < addMem.length; i++) {
          orgMem[i].push(addMem[i])
        }
      }

      this.teams = orgMem.map((e) => e.join('\n'))
    },
  },
}
</script>
