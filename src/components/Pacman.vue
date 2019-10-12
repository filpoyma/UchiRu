<template>
    <div class="container"
         :style="{height: `${getHeight()}px`, width: `${getWidth()}px`}">
        <div class="playground"
             :style="{height: `${getHeight()}px`}">
            <div class="pacman"
                 :style="{top: pacmanTop, left: pacmanLeft}">
            </div>
        </div>
        <div class="manage-box">
            <div class="arrow-up"
                 v-on:click="arrowButton($event)"
                 v-bind:style="{ borderBottom: keyUp }">
            </div>
            <div class="break"></div>
            <div class="arrow-left"
                 v-on:click="arrowButton($event)"
                 v-bind:style="{ borderRight: keyLeft }">

            </div>
            <div class="arrow-down"
                 v-on:click="arrowButton($event)"
                 v-bind:style="{ borderTop: keyDown }">

            </div>
            <div class="arrow-right"
                 v-on:click="arrowButton($event)"
                 v-bind:style="{ borderLeft: keyRight }">
            </div>
        </div>
    </div>
</template>

<script>
  const enabledKey = '20px solid black';
  const disabledKey = '20px solid gray';
  let top = window.innerHeight / 2 - 70;
  let left = window.innerWidth / 2 - 200;
  export default {
    name: 'Pacman',
    data: () => ({
      pacmanTop: `${top}px`,
      pacmanLeft: `${left}px`,
      keyUp: enabledKey,
      keyDown: enabledKey,
      keyLeft: enabledKey,
      keyRight: enabledKey
    }),
    methods: {
      arrowButton(e) {
        switch (e.path[0].className) {
          case 'arrow-up':
            if (top <= 30) {
              this.keyUp = disabledKey;
            } else {
              this.keyDown = enabledKey;
              this.pacmanTop = `${top -= 30}px`;
            }
            break;
          case
          'arrow-left':
            if (left <= 30) {
              this.keyLeft = disabledKey;
            } else {
              this.keyRight = enabledKey;
              this.pacmanLeft = `${left -= 30}px`;
            }
            break;
          case
          'arrow-down':
            if (top >= this.getHeight() - 160) {
              this.keyDown = disabledKey;
            } else {
              this.keyUp = enabledKey;
              this.pacmanTop = `${top += 20}px`;
            }
            break;
          case
          'arrow-right':
            if (left >= 80 * this.getWidth() / 100 - 135) {
              this.keyRight = disabledKey;
            } else {
              this.keyLeft = enabledKey;
              this.pacmanLeft = `${left += 20}px`;
            }
            break;
        }
      },
      getHeight() {
        return window.innerHeight;
      },
      getWidth() {
        return window.innerWidth;
      },
    },
  }
</script>

<style scoped>
    .pacman {
        width: 0;
        height: 0;
        position: absolute;
        border-right: 70px solid transparent;
        border-top: 70px solid #ffde00;
        border-left: 70px solid #ffde00;
        border-bottom: 70px solid #ffde00;
        border-top-left-radius: 70px;
        border-top-right-radius: 70px;
        border-bottom-left-radius: 70px;
        border-bottom-right-radius: 70px;
    }

    .container {
        display: flex;
        flex-direction: row;
    }

    .playground {
        width: 80%;
        background-color: #c7caca;
    }

    .manage-box {
        width: 20%;
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        align-items: center;
        align-content: center;
        justify-content: center;
    }

    .arrow-up {
        width: 0;
        height: 0;
        border-left: 20px solid transparent;
        border-right: 20px solid transparent;
    }

    .arrow-down {
        width: 0;
        height: 0;
        border-left: 20px solid transparent;
        border-right: 20px solid transparent;
        margin-top: 60px;
    }

    .arrow-right {
        width: 0;
        height: 0;
        border-top: 20px solid transparent;
        border-bottom: 20px solid transparent;
    }

    .arrow-left {
        width: 0;
        height: 0;
        border-top: 20px solid transparent;
        border-bottom: 20px solid transparent;
    }

    .break {
        flex-basis: 100%;
        height: 0;
    }
</style>
