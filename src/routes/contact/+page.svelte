<script>
	import { createBubbler, preventDefault } from 'svelte/legacy';
	const bubble = createBubbler();
	import Callout from '$lib/components/Callout.svelte';
</script>

<svelte:head>
	<title>Liên hệ</title>
</svelte:head>

<h1>Liên hệ với mình</h1>

Bạn muốn trao đổi, góp ý hoặc kết nối? Hãy để lại thông tin của bạn, mình sẽ liên hệ lại sớm nhất có thể.  
Bạn cũng có thể tìm thấy mình qua email: **tranhuyentrang@gmail.com** hoặc GitHub, LinkedIn.

<Callout>Form này hiện chỉ mang tính minh họa, chưa được kết nối backend.</Callout>

<form on:submit={preventDefault(bubble('submit'))}>
	<div class="form-section">
		<label for="name">Họ và tên</label>
		<input type="text" id="name" placeholder="Nhập họ tên của bạn" required />
	</div>
	
	<div class="form-section">
		<label for="email">Email</label>
		<input type="email" id="email" placeholder="Địa chỉ email" required />
	</div>

	<div class="form-section">
		<label for="phonenumber">Số điện thoại</label>
		<input type="phonenumber" id="phonenumber" placeholder="Số điện thoại" required />
	</div>

	<div class="form-section">
		<label for="message">Nội dung</label>
		<textarea id="message" rows="5" placeholder="Bạn muốn nhắn gì với mình?" required></textarea>
	</div>

	<fieldset>
		<legend>Bạn muốn mình phản hồi qua đâu?</legend>
		<div>
			<input type="radio" name="reply" id="reply-email" value="email" checked>
			<label for="reply-email">Email</label>
		</div>
		<div>
			<input type="radio" name="reply" id="reply-phone" value="phone">
			<label for="reply-phone">Số điện thoại</label>
		</div>
	</fieldset>

	<div class="form-section">
		<input type="checkbox" id="subscribe">
		<label for="subscribe">Gửi cho tôi bản tin nếu có bài viết mới</label>
	</div>

	<input type="submit" value="Gửi liên hệ">
</form>
