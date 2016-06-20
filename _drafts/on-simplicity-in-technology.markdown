<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
	<title>homepage</title>
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<link rel="stylesheet"  href="./dist/css/patternfly.min.css" media="screen, print">
	<link rel="stylesheet"  href="./dist/css/patternfly-additions.min.css" media="screen, print">
	<link rel="stylesheet"  href="./dist/css/form.css" media="screen, print">
</head>

<body class="overflow-h" >
	<div class="container-fluid">
		<div class="row row-h">
			<div class="col-md-12 col-sm-12 container-m result-content">
				<div class="result">
					<h1>My Records</h1>
					<table class="datatable table table-striped table-bordered table-hover">
						<thead>
							<tr>
								<th>ID</th>
								<th>category</th>
								<th>Create at</th>
								<th>State</th>
							</tr>
						</thead>
						<tbody>
							<tr class="gradeX">
								<td>DC1234432</td>
								<td>Docker Container Request</td>
								<td>2016/05/18 15:51</td>
								<td>
									<span class="pkg-status pkg-status-submitted">SUBMITTED</span>
								</td>
							</tr>
							<tr class="gradeX">
								<td>DC1234656</td>
								<td>Add an SCL</td>
								<td>2016/04/01 15:53</td>
								<td>
									<span class="pkg-status pkg-status-done">DONE</span>
								</td>
							</tr>
							<tr class="gradeX">
								<td>DC1234243</td>
								<td>Docker Container Request</td>
								<td>2016/04/04 10:22</td>
								<td>
									<span class="pkg-status pkg-status-submitted">SUBMITTED</span>
								</td>
							</tr>
							<tr class="gradeX">
								<td>DC1234435</td>
								<td>Docker Container Request</td>
								<td>2016/04/04 17:13</td>
								<td>
									<span class="pkg-status pkg-status-done">DONE</span>
								</td>
							</tr>
							<tr class="gradeX">
								<td>DC1234242</td>
								<td>Docker Container Request</td>
								<td>2016/04/29 15:02</td>
								<td>
									<span class="pkg-status pkg-status-in-progress-o">IN PROGRESS</span>
								</td>
							</tr>
						<tr class="gradeX">
								<td>DC1234495</td>
								<td>Docker Container Request</td>
								<td>2016/04/04 17:32</td>
								<td>
									<span class="pkg-status pkg-status-done">DONE</span>
								</td>
							</tr>
							<tr class="gradeX">
								<td>DC1234489</td>
								<td>Others</td>
								<td>2016/04/07 16:32</td>
								<td>
									<span class="pkg-status pkg-status-done">DONE</span>
								</td>
							</tr>
							<tr class="gradeX">
								<td>DC1234787</td>
								<td>Signing Privileges</td>
								<td>2016/05/04 12:05</td>
								<td>
									<span class="pkg-status pkg-status-done">DONE</span>
								</td>
							</tr>
							<tr class="gradeX">
								<td>DC1234097</td>
								<td>Add an SCL</td>
								<td>2016/04/04 16:32</td>
								<td>
									<span class="pkg-status pkg-status-canceled">CANCELED</span>
								</td>
							</tr>
							<tr class="gradeX">
								<td>DC1234347</td>
								<td>Change Component Owner</td>
								<td>2016/04/04 16:32</td>
								<td>
									<span class="pkg-status pkg-status-done">DONE</span>
								</td>
							</tr>
						</tbody>
					</table>
				</div>
			</div>
		</div>
	</div>

	
	<script src="./components/jquery/dist/jquery.min.js"></script>
	<script src="./components/bootstrap/dist/js/bootstrap.min.js"></script>
	<script src="./components/datatables/media/js/jquery.dataTables.js"></script>
	<script src="./dist/js/patternfly.min.js"></script>
	<script>
		(function($){
			$(document).ready(function(){
				$(".search-pf .has-clear .clear").each(function(){
					if (!$(this).prev('.form-control').val()){
						$(this).hide();
					}
				});

				$(".search-pf .has-clear .form-control").keyup(function(){
					var t=$(this);
					t.next('button').toggle(Boolean(t.val()));
				});
				$(".search-pf .has-clear .clear").click(function(){
					$(this).prev('.form-control').val('').focus();
					$(this).hide();
				});
			});
		})(jQuery);
	</script>

	<script>
		$(document).ready(function(){
			$('.datatable').dataTable({
				"fnDrawCallback":function(oSettings){
					if ($('.sidebar-pf').length > 0) {
						$(document).sidebar();
					}
				}
			});
		});
	</script>


</body>
</html>