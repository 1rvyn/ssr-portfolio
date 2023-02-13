<script>
    import dayjs from 'dayjs';
    let age = '';

  // Calculate age every second
  setInterval(() => {
    const birthDate = dayjs('2001-11-28');
    age = dayjs().diff(birthDate, 'year', true).toFixed(9);
  }, 50);
</script>

<span>{age}</span>