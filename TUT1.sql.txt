select date(crateddate), (sum(dr_amount) - sum(cr_amount)) as outstanding_amount from    (


SELECT ld._id as loanid, product, --principal_outstanding: sum(dr_amount) - sum(cr_amount)
(CONVERT_TIMEZONE('Asia/Kolkata', TIMESTAMP 'epoch' + sanctiondate/1000 * INTERVAL '1 second')) as sanction_date,
(CONVERT_TIMEZONE('Asia/Kolkata', TIMESTAMP 'epoch' + loandisburseddate/1000 * INTERVAL '1 second')) as disbursal_date,
(CONVERT_TIMEZONE('Asia/Kolkata', TIMESTAMP 'epoch' + date/1000 * INTERVAL '1 second')) as asofdate,  dr_amount, cr_amount


from loan ld 
left join journal lj on lj._id = ld._id 


where asofdate<'2023-05-01' and product = 'MARRIAGE_LOAN' 

 GROUP BY 1 
