<script>
    export let nums = "";

    let buttons = Array(12);

    const KEYCODE_BACKSPACE = 8;
    const KEYCODE_DELETE = 46;
    const KEYCODE_NUM_MIN = 48;
    const KEYCODE_NUM_MAX = 57;
    const KEYCODE_NUMPAD_MIN = 96;
    const KEYCODE_NUMPAD_MAX = 105;

    const handleClickNum = (num) => () => {
        addNum(num);
    };

    const addNum = (num) => {
        nums += num;
        //FIXME set focus after a mouse click so that user can tell which button is in focus since [Enter] presses the button currenly in focus.
        buttons[num].focus();
    };

    const del = () => {
        nums = nums.slice(0, nums.length - 1);
        buttons[11].focus();
    };

    const clear = () => {
        nums = "";
        buttons[10].focus();
    };

    function isNumberKey(keyCode) {
        return (
            (keyCode >= KEYCODE_NUM_MIN && keyCode <= KEYCODE_NUM_MAX) ||
            (keyCode >= KEYCODE_NUMPAD_MIN && keyCode <= KEYCODE_NUMPAD_MAX)
        );
    }

    function handleKeydown(event) {
        let keyCode = event.keyCode;
        let key = event.key;
        if (isNumberKey(keyCode)) {
            addNum(key);
        } else if (keyCode == KEYCODE_DELETE) {
            clear();
        } else if (keyCode == KEYCODE_BACKSPACE) {
            del();
        }
    }
</script>

<svelte:window on:keydown={handleKeydown} />

<div class="d-flex p-2 justify-content-center">
    <div class="numberpad-container">
        <div class="numberpad">
            {#each Array(9) as _, i}
                <button
                    on:click={handleClickNum(9 - i)}
                    bind:this={buttons[9 - i]}>{9 - i}</button
                >
            {/each}
            <button on:click={clear} bind:this={buttons[10]}
                ><i class="fas fa-trash-alt" /></button
            >
            <button on:click={handleClickNum(0)} bind:this={buttons[0]}
                >0</button
            >
            <button on:click={del} bind:this={buttons[11]}
                ><i class="fas fa-backspace" /></button
            >
        </div>
    </div>
</div>

<style>
    .numberpad-container {
        width: 260px;
        text-align: center;
    }
    .numberpad {
        display: grid;
        grid-template-columns: repeat(3, 5em);
        grid-template-rows: repeat(4, 3em);
        grid-gap: 0.5em;
        direction: rtl;
    }
</style>
