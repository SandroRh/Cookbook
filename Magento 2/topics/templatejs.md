## Exemplo

```javascript
<script type="text/javascript">
    require(["jquery"], function ($) {
        $('.increaseQty, .decreaseQty').on("click", function () {
            let inputElem = $(this).parents('td').find('input');
            let currentQty = inputElem.val();
            if ($(this).hasClass('increaseQty')) {
                inputElem.val(parseInt(currentQty) + parseInt(1));
            } else {
                if (currentQty > 1) {
                    inputElem.val(parseInt(currentQty) - parseInt(1));
                }
            }
            $("#form-validate").submit();
        });
    });
</script>
```